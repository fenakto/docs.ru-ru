---
title: "Одностороннее взаимодействие | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 74e3e03d-cd15-4191-a6a5-1efa2dcb9e73
caps.latest.revision: 26
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 26
---
# Одностороннее взаимодействие
В этом образце демонстрируется контакт службы с односторонними операциями службы.Клиент не ожидает завершения операций службы, как это происходит в случае двусторонних операций службы.Этот образец основан на [Начало работы](../../../../docs/framework/wcf/samples/getting-started-sample.md) и использует привязку `wsHttpBinding`.В данном образце служба представляет собой резидентное консольное приложение, позволяющее наблюдать за тем, как служба получает и обрабатывает запросы.Клиент также является консольным приложением.  
  
> [!NOTE]
>  Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.  
  
 Чтобы создать односторонний контракт службы, определите контракт службы, примените класс <xref:System.ServiceModel.OperationContractAttribute> к каждой из операций и присвойте свойству <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> логическое значение `true`, как показано в следующем образце кода:  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOneWayCalculator  
{  
    [OperationContract(IsOneWay=true)]  
    void Add(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Subtract(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Multiply(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Divide(double n1, double n2);  
}  
  
```  
  
 В следующем образце кода показано, что клиент не ждет момента завершения операций службы. Для наглядной демонстрации код службы реализует пятисекундную задержку:  
  
```  
/ This service class implements the service contract.  
// This code writes output to the console window.  
 [ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Multiple,  
    InstanceContextMode = InstanceContextMode.PerCall)]  
public class CalculatorService : IOneWayCalculator  
{  
    public void Add(double n1, double n2)  
    {  
        Console.WriteLine("Received Add({0},{1}) - sleeping", n1, n2);  
        System.Threading.Thread.Sleep(1000 * 5);  
        double result = n1 + n2;  
        Console.WriteLine("Processing Add({0},{1}) - result: {2}", n1, n2, result);  
    }  
    ...  
}  
  
```  
  
 Когда клиент вызывает службу, вызов возвращается без ожидания завершения операции службы.  
  
 При выполнении образца действия клиента и службы отображаются в окнах консоли как службы, так и клиента.Можно видеть, как служба получает сообщения от клиента.Нажмите клавишу ВВОД в каждом окне консоли, чтобы закрыть и службу, и клиент.  
  
 Клиент завершает работу раньше службы, демонстрируя таким образом, что клиент не ожидает завершения односторонних операций службы.Результат работы клиента имеет следующий вид:  
  
```  
Add(100,15.99)  
Subtract(145,76.54)  
Multiply(9,81.25)  
Divide(22,7)  
  
Press <ENTER> to terminate client.  
  
```  
  
 Показан следующий результат работы службы:  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Received Add(100,15.99) - sleeping  
Received Subtract(145,76.54) - sleeping  
Received Multiply(9,81.25) - sleeping  
Received Divide(22,7) - sleeping  
Processing Add(100,15.99) - result: 115.99  
Processing Subtract(145,76.54) - result: 68.46  
Processing Multiply(9,81.25) - result: 731.25  
Processing Divide(22,7) - result: 3.14285714285714  
  
```  
  
> [!NOTE]
>  HTTP, по определению, является протоколом запроса\-ответа. На переданный запрос должен быть возвращен ответ.Это справедливо даже для односторонней операции службы, предоставляемой через HTTP.При вызове операции служба возвращает код состояния HTTP 202 до момента, когда операция службы уже выполнена.Этот код состояния означает, что запрос принят для обработки, но обработка еще не была закончена.Вызвавший операцию клиент блокируется до момента получения ответа 202 от службы.Это может являться причиной непредвиденного поведения, когда передано множество односторонних сообщений с использованием привязки, которая сконфигурирована для использования сеансов.Использованная в этом образце привязка `wsHttpBinding` по умолчанию сконфигурирована для использования сеансов, чтобы устанавливать контекст безопасности.По умолчанию сообщения в сеансе прибывают точно в том порядке, в котором отправлены.По этой причине не обрабатывается второе переданное в сеансе сообщение, пока не обработано первое сообщение.В результате клиент не получает ответ 202 для текущего сообщения до момента завершения обработки предыдущего сообщения.Поэтому клиент блокируется для каждого последующего вызов операции.Для предотвращения такого поведения этот образец конфигурирует среду выполнения таким образом, чтобы одновременно определить сообщения различным экземплярам для обработки.Образец устанавливает свойству <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> значение `PerCall`, чтобы каждое сообщение обрабатывалось отдельным экземпляром.Свойству <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> задается значение `Multiple`, которое позволяет нескольким потокам одновременно распределять сообщения.  
  
### Настройка, построение и выполнение образца  
  
1.  Убедитесь, что выполнены процедуры, описанные в разделе [Процедура однократной настройки образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Чтобы создать выпуск решения на языке C\# или Visual Basic .NET, следуйте инструкциям в разделе [Построение образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Чтобы выполнить образец на одном или нескольких компьютерах, следуйте инструкциям раздела [Выполнение примеров Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
>  Запустите службу перед запуском клиента и завершите работу клиента перед завершением работы службы.Это предотвратит исключение для клиента, если клиент не может завершить сеанс безопасности без ошибок по причине отсутствия службы.  
  
> [!IMPORTANT]
>  Образцы уже могут быть установлены на компьютере.Перед продолжением проверьте следующий каталог \(по умолчанию\).  
>   
>  `<диск_установки>:\WF_WCF_Samples`  
>   
>  Если этот каталог не существует, перейдите на страницу [Образцы Windows Communication Foundation \(WCF\) и Windows Workflow Foundation \(WF\) для .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780), чтобы загрузить все образцы [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] и [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Этот образец расположен в следующем каталоге.  
>   
>  `<диск_установки>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Oneway`  
  
## См. также