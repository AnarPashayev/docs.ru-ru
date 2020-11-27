---
title: Использование средства привязки сериализации
ms.date: 03/30/2017
ms.assetid: ab46c087-200c-45bf-9c95-5a6cda6e8b98
ms.openlocfilehash: 061afb94d97e3d8a1222e6de9932344fb3ebbe59
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294902"
---
# <a name="usage-of-serialization-binder"></a><span data-ttu-id="ea322-102">Использование средства привязки сериализации</span><span class="sxs-lookup"><span data-stu-id="ea322-102">Usage of Serialization Binder</span></span>

<span data-ttu-id="ea322-103">В этом образце показано, как использовать <xref:System.Runtime.Serialization.SerializationBinder> для изменения версии универсального типа во время сериализации.</span><span class="sxs-lookup"><span data-stu-id="ea322-103">This sample shows how to use the <xref:System.Runtime.Serialization.SerializationBinder> to change the version of a generic type when it is serialized.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="ea322-104">Что демонстрирует</span><span class="sxs-lookup"><span data-stu-id="ea322-104">Demonstrates</span></span>  

 <span data-ttu-id="ea322-105"><xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter></span><span class="sxs-lookup"><span data-stu-id="ea322-105"><xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="ea322-106">Разговор</span><span class="sxs-lookup"><span data-stu-id="ea322-106">Discussion</span></span>  

 <span data-ttu-id="ea322-107">В этом примере показано, как две сущности, предназначенные для разных версий .NET Framework, могут взаимодействовать с помощью двоичного модуля форматирования и связывателя сериализации.</span><span class="sxs-lookup"><span data-stu-id="ea322-107">This sample shows how two entities that are targeting different versions of the .NET Framework can communicate using the binary formatter and the serialization binder.</span></span>  
  
<span data-ttu-id="ea322-108">Этот пример был разработан с помощью удаленного взаимодействия .NET.</span><span class="sxs-lookup"><span data-stu-id="ea322-108">This sample was developed using .NET Remoting.</span></span> <span data-ttu-id="ea322-109">Он состоит из сервера, предназначенного для .NET Framework 4, который реализует контракт с универсальными типами и двумя разными клиентами, один предназначен для .NET Framework 2,0 и другой целевой .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="ea322-109">It consists of a server targeting .NET Framework 4, which implements a contract with generic types, and two different clients, one targeting .NET Framework 2.0 and another targeting .NET Framework 4.</span></span>  
  
 <span data-ttu-id="ea322-110">Сервер присоединяет средство привязки <xref:System.Runtime.Serialization.SerializationBinder> к двоичному форматировщику, чтобы иметь возможность соответствующим образом изменять версию типов при сериализации, в результате чего оба клиента смогут правильно десериализовать эти типы.</span><span class="sxs-lookup"><span data-stu-id="ea322-110">The server attaches a <xref:System.Runtime.Serialization.SerializationBinder> to the binary formatter to be able to change the version of the types accordingly on serialization, so both clients can deserialize those types properly.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ea322-111">Настройка, построение и выполнение примера</span><span class="sxs-lookup"><span data-stu-id="ea322-111">To set up, build and run the sample</span></span>  
  
1. <span data-ttu-id="ea322-112">Чтобы выполнить клиент, щелкните правой кнопкой мыши решение Сбженериксвтс (6 проектов) и выберите пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="ea322-112">To execute the client, right-click the solution, SBGenericsVTS (6 projects) and then select **Properties**.</span></span>  
  
2. <span data-ttu-id="ea322-113">В окне **Общие свойства** выберите **запускаемый проект**, а затем выберите **Несколько запускаемых проектов**.</span><span class="sxs-lookup"><span data-stu-id="ea322-113">In **Common Properties**, select **Startup Project**, then select **Multiple Startup Projects**.</span></span>  
  
3. <span data-ttu-id="ea322-114">Сначала выберите **сервер** , затем **Client20** , а затем **Client40**.</span><span class="sxs-lookup"><span data-stu-id="ea322-114">Select **Server** first, then **Client20** and then **Client40**.</span></span> <span data-ttu-id="ea322-115">Выберите действие **Запуск** для этих трех проектов и оставьте для параметра остальные значение **нет**.</span><span class="sxs-lookup"><span data-stu-id="ea322-115">Select the **Start** action to these three projects and leave the rest set to **None**.</span></span>  
  
4. <span data-ttu-id="ea322-116">Нажмите кнопку **ОК** , а затем нажмите клавишу F5, чтобы запустить пример.</span><span class="sxs-lookup"><span data-stu-id="ea322-116">Click **OK** and then press F5 to run the sample.</span></span>
