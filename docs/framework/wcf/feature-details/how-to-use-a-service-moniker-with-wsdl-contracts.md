---
title: Практическое руководство. Использование моникера службы с контрактами WSDL
ms.date: 03/30/2017
ms.assetid: a88d9650-bb50-4f48-8c85-12f5ce98a83a
ms.openlocfilehash: 70d7e9ff45616f832597ebc48db00198967935c6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601144"
---
# <a name="how-to-use-a-service-moniker-with-wsdl-contracts"></a><span data-ttu-id="a133e-102">Практическое руководство. Использование моникера службы с контрактами WSDL</span><span class="sxs-lookup"><span data-stu-id="a133e-102">How to: Use a Service Moniker with WSDL Contracts</span></span>
<span data-ttu-id="a133e-103">Существуют ситуации, когда требуется полностью автономный клиент COM-взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="a133e-103">There are situations when you may want to have a completely self-contained COM Interop client.</span></span> <span data-ttu-id="a133e-104">Например, вызываемая служба может не отображать конечную точку обмена метаданными, а клиентская библиотека WCF может быть не зарегистрирована для COM-взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="a133e-104">The service you want to call may not expose a MEX endpoint, and the WCF client DLL may not be registered for COM interop.</span></span> <span data-ttu-id="a133e-105">В таких ситуациях можно создать WSDL-файл, описывающий службу, и передать его в моникер службы WCF.</span><span class="sxs-lookup"><span data-stu-id="a133e-105">In these cases, you can create a WSDL file that describes the service and pass it into the WCF service moniker.</span></span> <span data-ttu-id="a133e-106">В данном разделе описывается, как вызвать образец WCF "Приступая к работе" с помощью моникера WSDL для службы WCF.</span><span class="sxs-lookup"><span data-stu-id="a133e-106">This topic describes how to call the Getting Started WCF sample using a WCF WSDL moniker.</span></span>  
  
### <a name="using-the-wsdl-service-moniker"></a><span data-ttu-id="a133e-107">Использование моникера WSDL</span><span class="sxs-lookup"><span data-stu-id="a133e-107">Using the WSDL service moniker</span></span>  
  
1. <span data-ttu-id="a133e-108">Откройте и постройте образец решения "Приступая к работе".</span><span class="sxs-lookup"><span data-stu-id="a133e-108">Open and build the GettingStarted sample solution.</span></span>  
  
2. <span data-ttu-id="a133e-109">Откройте Internet Explorer и перейдите к `http://localhost/ServiceModelSamples/Service.svc` , чтобы убедиться, что служба работает.</span><span class="sxs-lookup"><span data-stu-id="a133e-109">Open Internet Explorer and browse to `http://localhost/ServiceModelSamples/Service.svc` to make sure that the service is working.</span></span>  
  
3. <span data-ttu-id="a133e-110">В файле Service.cs добавьте следующий атрибут в класс CalculatorService:</span><span class="sxs-lookup"><span data-stu-id="a133e-110">In the Service.cs file, add the following attribute on the CalculatorService class:</span></span>  
  
     [!code-csharp[S_WSDL_Client#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wsdl_client/cs/service.cs#0)]  
  
4. <span data-ttu-id="a133e-111">Добавьте пространство имен привязки в файл конфигурации службы App.config:</span><span class="sxs-lookup"><span data-stu-id="a133e-111">Add a binding namespace to the service App.config:</span></span>  

5. <span data-ttu-id="a133e-112">Создайте WSDL-файл для считывания приложением.</span><span class="sxs-lookup"><span data-stu-id="a133e-112">Create a WSDL file for the application to read.</span></span> <span data-ttu-id="a133e-113">Так как пространства имен были добавлены в шагах 3 и 4, можно использовать IE для запроса полного описания WSDL службы, перейдя по адресу `http://localhost/ServiceModelSamples/Service.svc?wsdl` .</span><span class="sxs-lookup"><span data-stu-id="a133e-113">Because the namespaces were added in steps 3 and 4, you can use IE to query for the entire WSDL description of the service by browsing to `http://localhost/ServiceModelSamples/Service.svc?wsdl`.</span></span> <span data-ttu-id="a133e-114">Файл из Internet Explorer можно сохранить с именем serviceWSDL.xml.</span><span class="sxs-lookup"><span data-stu-id="a133e-114">You can then save the file from Internet Explorer as serviceWSDL.xml.</span></span> <span data-ttu-id="a133e-115">Если на шагах 3 и 4 не было указано пространство имен, документ WSDL, возвращаемый после запроса вышеуказанного URL-адреса, будет не полным.</span><span class="sxs-lookup"><span data-stu-id="a133e-115">If you do not specify the namespaces in steps 3 and 4, the WSDL document returned from querying the above URL will not be the complete WSDL.</span></span> <span data-ttu-id="a133e-116">Возвращаемый документ WSDL будет содержать несколько операторов импорта, с помощью которых выполняется импорт других документов WSDL.</span><span class="sxs-lookup"><span data-stu-id="a133e-116">The WSDL document returned will include several import statements that import other WSDL documents.</span></span> <span data-ttu-id="a133e-117">Необходимо пройти все операторы импорта и построить полный документ WSDL, объединяющий как данные, полученные из службы, так и импортированные документы WSDL.</span><span class="sxs-lookup"><span data-stu-id="a133e-117">You will have to go through each import statement and build the complete WSDL document, combining the WSDL returned from the service with the WSDL imported.</span></span>  
  
6. <span data-ttu-id="a133e-118">Откройте Visual Basic 6.0 и создайте новый стандартный EXE-файл.</span><span class="sxs-lookup"><span data-stu-id="a133e-118">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="a133e-119">Добавьте в форму кнопку и дважды щелкните ее, чтобы добавить следующий код в обработчик щелчка.</span><span class="sxs-lookup"><span data-stu-id="a133e-119">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
    ```vb
    ' Open the WSDL contract file and read it all into the wsdlContract string.  
    Const ForReading = 1  
    Set objFSO = CreateObject("Scripting.FileSystemObject")  
    Set objFile = objFSO.OpenTextFile("c:\serviceWsdl.xml", ForReading)  
    wsdlContract = objFile.ReadAll  
    objFile.Close  
  
    ' Create a string for the service moniker including the content of the WSDL contract file.  
    wsdlMonikerString = "service4:address='http://localhost/ServiceModelSamples/service.svc'"  
    wsdlMonikerString = wsdlMonikerString + ", wsdl='" & wsdlContract & "'"  
    wsdlMonikerString = wsdlMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
    wsdlMonikerString = wsdlMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
    ' Create the service moniker object.  
    Set wsdlServiceMoniker = GetObject(wsdlMonikerString)  
  
    ' Call the service operations using the moniker object.  
    MsgBox "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
    ```  
  
    > [!NOTE]
    > Если неправильно сформирован моникер или служба недоступна, при вызове `GetObject` будет получена ошибка "Синтаксическая ошибка".  <span data-ttu-id="a133e-121">При получении этой ошибки убедитесь, что используется правильный моникер, а служба доступна.</span><span class="sxs-lookup"><span data-stu-id="a133e-121">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
7. <span data-ttu-id="a133e-122">Запустите приложение Visual Basic 6.0.</span><span class="sxs-lookup"><span data-stu-id="a133e-122">Run the Visual Basic application.</span></span> <span data-ttu-id="a133e-123">Отобразится окно сообщения с результатами вызова Subtract(145, 76.54).</span><span class="sxs-lookup"><span data-stu-id="a133e-123">A message box will be displayed with the results of calling Subtract(145, 76.54).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a133e-124">Дополнительно</span><span class="sxs-lookup"><span data-stu-id="a133e-124">See also</span></span>

- [<span data-ttu-id="a133e-125">Начало работы</span><span class="sxs-lookup"><span data-stu-id="a133e-125">Getting Started</span></span>](../samples/getting-started-sample.md)
- [<span data-ttu-id="a133e-126">Общие сведения об интеграции с приложениями COM</span><span class="sxs-lookup"><span data-stu-id="a133e-126">Integrating with COM Applications Overview</span></span>](integrating-with-com-applications-overview.md)
