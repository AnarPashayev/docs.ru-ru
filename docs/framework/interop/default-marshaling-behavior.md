---
title: Поведение маршалинга по умолчанию
ms.date: 06/26/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interop marshaling, default
- interoperation with unmanaged code, marshaling
- marshaling behavior
ms.assetid: c0a9bcdf-3df8-4db3-b1b6-abbdb2af809a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a057f872d15ca1fcd49d86d08606776a0c0bea0
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063318"
---
# <a name="default-marshaling-behavior"></a><span data-ttu-id="9a918-102">Поведение маршалинга по умолчанию</span><span class="sxs-lookup"><span data-stu-id="9a918-102">Default Marshaling Behavior</span></span>
<span data-ttu-id="9a918-103">Маршалинг взаимодействия работает по правилам, которые определяют поведение данных, связанных с параметрами метода, при их передаче между управляемой и неуправляемой памятью.</span><span class="sxs-lookup"><span data-stu-id="9a918-103">Interop marshaling operates on rules that dictate how data associated with method parameters behaves as it passes between managed and unmanaged memory.</span></span> <span data-ttu-id="9a918-104">Эти встроенные правила определяют такие операции маршалинга, как преобразования типов данных, возможность изменения вызываемым объектом переданных ему данных и возврата этих изменений вызывающему объекту, а также обстоятельства, при которых упаковщик обеспечивает оптимизацию производительности.</span><span class="sxs-lookup"><span data-stu-id="9a918-104">These built-in rules control such marshaling activities as data type transformations, whether a callee can change data passed to it and return those changes to the caller, and under which circumstances the marshaler provides performance optimizations.</span></span>  
  
 <span data-ttu-id="9a918-105">В этом разделе описаны стандартные характеристики службы маршалинга взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="9a918-105">This section identifies the default behavioral characteristics of the interop marshaling service.</span></span> <span data-ttu-id="9a918-106">Представлены подробные сведения о маршалинге массивов, логических типов, символьных типов, делегатов, классов, объектов, строк и структур.</span><span class="sxs-lookup"><span data-stu-id="9a918-106">It presents detailed information on marshaling arrays, Boolean types, char types, delegates, classes, objects, strings, and structures.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9a918-107">Маршалинг универсальных типов не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="9a918-107">Marshaling of generic types is not supported.</span></span> <span data-ttu-id="9a918-108">Дополнительные сведения см. в разделе [Взаимодействие с помощью универсальных типов](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="9a918-108">For more information see, [Interoperating Using Generic Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100)).</span></span>  
  
## <a name="memory-management-with-the-interop-marshaler"></a><span data-ttu-id="9a918-109">Управление памятью с помощью упаковщика взаимодействия</span><span class="sxs-lookup"><span data-stu-id="9a918-109">Memory management with the interop marshaler</span></span>  
 <span data-ttu-id="9a918-110">Упаковщик взаимодействия всегда пытается освободить память, распределенную неуправляемым кодом.</span><span class="sxs-lookup"><span data-stu-id="9a918-110">The interop marshaler always attempts to free memory allocated by unmanaged code.</span></span> <span data-ttu-id="9a918-111">Такое поведение согласуется с правилами управления памятью COM, но отличается от правил, присущих C++.</span><span class="sxs-lookup"><span data-stu-id="9a918-111">This behavior complies with COM memory management rules, but differs from the rules that govern native C++.</span></span>  
  
 <span data-ttu-id="9a918-112">Путаница может возникать, если ожидается поведение в стиле C++ (память не освобождается) при вызове неуправляемого кода, при котором память автоматически освобождается для указателей.</span><span class="sxs-lookup"><span data-stu-id="9a918-112">Confusion can arise if you anticipate native C++ behavior (no memory freeing) when using platform invoke, which automatically frees memory for pointers.</span></span> <span data-ttu-id="9a918-113">Например, вызов приведенного ниже неуправляемого метода из библиотеки DLL C++ не освобождает память автоматически.</span><span class="sxs-lookup"><span data-stu-id="9a918-113">For example, calling the following unmanaged method from a C++ DLL does not automatically free any memory.</span></span>  
  
### <a name="unmanaged-signature"></a><span data-ttu-id="9a918-114">Неуправляемая сигнатура</span><span class="sxs-lookup"><span data-stu-id="9a918-114">Unmanaged signature</span></span>  
  
```cpp  
BSTR MethodOne (BSTR b) {  
     return b;  
}  
```  
  
 <span data-ttu-id="9a918-115">Однако если при определении метода в качестве прототипа вызова неуправляемого кода заменить каждый тип **BSTR** на тип <xref:System.String> и вызвать `MethodOne`, среда CLR дважды попытается освободить `b`.</span><span class="sxs-lookup"><span data-stu-id="9a918-115">However, if you define the method as a platform invoke prototype, replace each **BSTR** type with a <xref:System.String> type, and call `MethodOne`, the common language runtime attempts to free `b` twice.</span></span> <span data-ttu-id="9a918-116">Поведение маршалинга можно изменить с помощью типов <xref:System.IntPtr>, а не типов **String**.</span><span class="sxs-lookup"><span data-stu-id="9a918-116">You can change the marshaling behavior by using <xref:System.IntPtr> types rather than **String** types.</span></span>  
  
 <span data-ttu-id="9a918-117">Среда выполнения всегда использует метод **CoTaskMemFree** для освобождения памяти.</span><span class="sxs-lookup"><span data-stu-id="9a918-117">The runtime always uses the **CoTaskMemFree** method to free memory.</span></span> <span data-ttu-id="9a918-118">Если память, с которой работает программа, не была выделена с помощью метода **CoTaskMemAlloc**, то необходимо использовать **IntPtr** и освободить память вручную с применением подходящего метода.</span><span class="sxs-lookup"><span data-stu-id="9a918-118">If the memory you are working with was not allocated with the **CoTaskMemAlloc** method, you must use an **IntPtr** and free the memory manually using the appropriate method.</span></span> <span data-ttu-id="9a918-119">Аналогичным образом можно избежать автоматического освобождения памяти в ситуациях, когда память ни при каких обстоятельствах не должна освобождаться, например при использовании функции **GetCommandLine** из Kernel32.dll, которая возвращает указатель в память ядра.</span><span class="sxs-lookup"><span data-stu-id="9a918-119">Similarly, you can avoid automatic memory freeing in situations where memory should never be freed, such as when using the **GetCommandLine** function from Kernel32.dll, which returns a pointer to kernel memory.</span></span> <span data-ttu-id="9a918-120">Подробнее об освобождении памяти вручную см. в разделе [Пример буферов](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x3txb6xc(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="9a918-120">For details on manually freeing memory, see the [Buffers Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x3txb6xc(v=vs.100)).</span></span>  
  
## <a name="default-marshaling-for-classes"></a><span data-ttu-id="9a918-121">Маршалинг по умолчанию для классов</span><span class="sxs-lookup"><span data-stu-id="9a918-121">Default marshaling for classes</span></span>  
 <span data-ttu-id="9a918-122">Маршалинг классов может выполняться только с помощью COM-взаимодействия и только в качестве интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="9a918-122">Classes can be marshaled only by COM interop and are always marshaled as interfaces.</span></span> <span data-ttu-id="9a918-123">Иногда интерфейс, используемый для маршалинга класса, называют интерфейсом класса.</span><span class="sxs-lookup"><span data-stu-id="9a918-123">In some cases the interface used to marshal the class is known as the class interface.</span></span> <span data-ttu-id="9a918-124">Подробнее о переопределении интерфейса класса другим выбранным интерфейсом см. в статье [Introducing the class interface](com-callable-wrapper.md#introducing-the-class-interface) (Введение в интерфейс класса).</span><span class="sxs-lookup"><span data-stu-id="9a918-124">For information about overriding the class interface with an interface of your choice, see [Introducing the class interface](com-callable-wrapper.md#introducing-the-class-interface).</span></span>  
  
### <a name="passing-classes-to-com"></a><span data-ttu-id="9a918-125">Передача классов в COM</span><span class="sxs-lookup"><span data-stu-id="9a918-125">Passing Classes to COM</span></span>  
 <span data-ttu-id="9a918-126">При передаче управляемого класса в COM упаковщик взаимодействия автоматически инкапсулирует этот класс, используя COM-прокси, и передает интерфейс класса, полученный с помощью прокси, в вызов метода COM.</span><span class="sxs-lookup"><span data-stu-id="9a918-126">When a managed class is passed to COM, the interop marshaler automatically wraps the class with a COM proxy and passes the class interface produced by the proxy to the COM method call.</span></span> <span data-ttu-id="9a918-127">Затем прокси делегирует все вызовы для интерфейса класса назад в управляемый объект.</span><span class="sxs-lookup"><span data-stu-id="9a918-127">The proxy then delegates all calls on the class interface back to the managed object.</span></span> <span data-ttu-id="9a918-128">Прокси также предоставляет другие интерфейсы, которые не реализованы классом явным образом.</span><span class="sxs-lookup"><span data-stu-id="9a918-128">The proxy also exposes other interfaces that are not explicitly implemented by the class.</span></span> <span data-ttu-id="9a918-129">Прокси от имени класса автоматически реализует такие интерфейсы, как **IUnknown** и **IDispatch**.</span><span class="sxs-lookup"><span data-stu-id="9a918-129">The proxy automatically implements interfaces such as **IUnknown** and **IDispatch** on behalf of the class.</span></span>  
  
### <a name="passing-classes-to-net-code"></a><span data-ttu-id="9a918-130">Передача классов в код .NET</span><span class="sxs-lookup"><span data-stu-id="9a918-130">Passing Classes to .NET Code</span></span>  
 <span data-ttu-id="9a918-131">В COM коклассы обычно не используются в качестве аргументов метода.</span><span class="sxs-lookup"><span data-stu-id="9a918-131">Coclasses are not typically used as method arguments in COM.</span></span> <span data-ttu-id="9a918-132">Вместо кокласса обычно передается интерфейс по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="9a918-132">Instead, a default interface is usually passed in place of the coclass.</span></span>  
  
 <span data-ttu-id="9a918-133">При передаче интерфейса в управляемый код упаковщик взаимодействия отвечает за инкапсуляцию интерфейса в соответствующую оболочку и за передачу этой оболочки в управляемый метод.</span><span class="sxs-lookup"><span data-stu-id="9a918-133">When an interface is passed into managed code, the interop marshaler is responsible for wrapping the interface with the proper wrapper and passing the wrapper to the managed method.</span></span> <span data-ttu-id="9a918-134">Выбор используемой оболочки может вызывать затруднения.</span><span class="sxs-lookup"><span data-stu-id="9a918-134">Determining which wrapper to use can be difficult.</span></span> <span data-ttu-id="9a918-135">У каждого экземпляра COM-объекта есть одна уникальная оболочка вне зависимости от числа интерфейсов, реализуемых объектом.</span><span class="sxs-lookup"><span data-stu-id="9a918-135">Every instance of a COM object has a single, unique wrapper, no matter how many interfaces the object implements.</span></span> <span data-ttu-id="9a918-136">Например, COM-объект, реализующий пять различных интерфейсов, имеет только одну оболочку.</span><span class="sxs-lookup"><span data-stu-id="9a918-136">For example, a single COM object that implements five distinct interfaces has only one wrapper.</span></span> <span data-ttu-id="9a918-137">Одна и та же оболочка предоставляет все пять интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="9a918-137">The same wrapper exposes all five interfaces.</span></span> <span data-ttu-id="9a918-138">Если создаются два экземпляра COM-объекта, то создаются и два экземпляра оболочки.</span><span class="sxs-lookup"><span data-stu-id="9a918-138">If two instances of the COM object are created, then two instances of the wrapper are created.</span></span>  
  
 <span data-ttu-id="9a918-139">Чтобы тип оболочки не менялся в течение всего времени ее существования, упаковщик взаимодействия должен выбрать правильную оболочку при первой передаче интерфейса, предоставляемого данным объектом, через упаковщик.</span><span class="sxs-lookup"><span data-stu-id="9a918-139">For the wrapper to maintain the same type throughout its lifetime, the interop marshaler must identify the correct wrapper the first time an interface exposed by the object is passed through the marshaler.</span></span> <span data-ttu-id="9a918-140">Упаковщик идентифицирует объект, просматривая один из интерфейсов, реализуемых объектом.</span><span class="sxs-lookup"><span data-stu-id="9a918-140">The marshaler identifies the object by looking at one of the interfaces the object implements.</span></span>  
  
 <span data-ttu-id="9a918-141">Например, упаковщик определяет, что оболочка класса должна использоваться для инкапсуляции интерфейса, переданного в управляемый код.</span><span class="sxs-lookup"><span data-stu-id="9a918-141">For example, the marshaler determines that the class wrapper should be used to wrap the interface that was passed into managed code.</span></span> <span data-ttu-id="9a918-142">При первой передаче этого интерфейса через упаковщик последний проверяет, поступил ли этот интерфейс от известного объекта.</span><span class="sxs-lookup"><span data-stu-id="9a918-142">When the interface is first passed through the marshaler, the marshaler checks whether the interface is coming from a known object.</span></span> <span data-ttu-id="9a918-143">Эта проверка выполняется в двух случаях:</span><span class="sxs-lookup"><span data-stu-id="9a918-143">This check occurs in two situations:</span></span>  
  
- <span data-ttu-id="9a918-144">Интерфейс реализуется другим управляемым объектом, переданным в COM где-то в другом месте.</span><span class="sxs-lookup"><span data-stu-id="9a918-144">An interface is being implemented by another managed object that was passed to COM elsewhere.</span></span> <span data-ttu-id="9a918-145">Упаковщик может легко идентифицировать интерфейсы, предоставляемые управляемыми объектами, и может находить соответствие между интерфейсом и управляемым объектом, предоставившим реализацию.</span><span class="sxs-lookup"><span data-stu-id="9a918-145">The marshaler can readily identify interfaces exposed by managed objects and is able to match the interface with the managed object that provides the implementation.</span></span> <span data-ttu-id="9a918-146">Затем управляемый объект передается в метод, и никакой оболочки не требуется.</span><span class="sxs-lookup"><span data-stu-id="9a918-146">The managed object is then passed to the method and no wrapper is needed.</span></span>  
  
- <span data-ttu-id="9a918-147">Интерфейс реализуется объектом, который уже инкапсулирован.</span><span class="sxs-lookup"><span data-stu-id="9a918-147">An object that has already been wrapped is implementing the interface.</span></span> <span data-ttu-id="9a918-148">Чтобы определить, так ли это, упаковщик запрашивает у объекта его интерфейс **IUnknown** и сравнивает возвращенный интерфейс с интерфейсами других, уже инкапсулированных объектов.</span><span class="sxs-lookup"><span data-stu-id="9a918-148">To determine whether this is the case, the marshaler queries the object for its **IUnknown** interface and compares the returned interface to the interfaces of other objects that are already wrapped.</span></span> <span data-ttu-id="9a918-149">Если интерфейс совпадает с интерфейсом другой оболочки, то объекты имеют одинаковые идентификаторы и существующая оболочка передается методу.</span><span class="sxs-lookup"><span data-stu-id="9a918-149">If the interface is the same as that of another wrapper, the objects have the same identity and the existing wrapper is passed to the method.</span></span>  
  
 <span data-ttu-id="9a918-150">Если интерфейс не является интерфейсом известного объекта, упаковщик выполняет указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="9a918-150">If an interface is not from a known object, the marshaler does the following:</span></span>  
  
1. <span data-ttu-id="9a918-151">Упаковщик запрашивает у объекта интерфейс **IProvideClassInfo2**.</span><span class="sxs-lookup"><span data-stu-id="9a918-151">The marshaler queries the object for the **IProvideClassInfo2** interface.</span></span> <span data-ttu-id="9a918-152">Если он предоставлен, то упаковщик использует значение CLSID, возвращенное из **IProvideClassInfo2.GetGUID**, для идентификации кокласса, предоставляющего интерфейс.</span><span class="sxs-lookup"><span data-stu-id="9a918-152">If provided, the marshaler uses the CLSID returned from **IProvideClassInfo2.GetGUID** to identify the coclass providing the interface.</span></span> <span data-ttu-id="9a918-153">Используя идентификатор CLSID, упаковщик может найти оболочку в реестре, если перед этим сборка была зарегистрирована.</span><span class="sxs-lookup"><span data-stu-id="9a918-153">With the CLSID, the marshaler can locate the wrapper from the registry if the assembly has previously been registered.</span></span>  
  
2. <span data-ttu-id="9a918-154">Упаковщик запрашивает у этого интерфейса интерфейс **IProvideClassInfo**.</span><span class="sxs-lookup"><span data-stu-id="9a918-154">The marshaler queries the interface for the **IProvideClassInfo** interface.</span></span> <span data-ttu-id="9a918-155">Если он предоставлен, упаковщик использует интерфейс **ITypeInfo**, возвращенный из метода **IProvideClassInfo.GetClassinfo**, для определения значения CLSID класса, предоставляющего интерфейс.</span><span class="sxs-lookup"><span data-stu-id="9a918-155">If provided, the marshaler uses the **ITypeInfo** returned from **IProvideClassInfo.GetClassinfo** to determine the CLSID of the class exposing the interface.</span></span> <span data-ttu-id="9a918-156">Упаковщик может использовать значение CLSID для нахождения метаданных оболочки.</span><span class="sxs-lookup"><span data-stu-id="9a918-156">The marshaler can use the CLSID to locate the metadata for the wrapper.</span></span>  
  
3. <span data-ttu-id="9a918-157">Если упаковщик все еще не может идентифицировать класс, то он инкапсулирует интерфейс в оболочку универсального класса с именем **System.__ComObject**.</span><span class="sxs-lookup"><span data-stu-id="9a918-157">If the marshaler still cannot identify the class, it wraps the interface with a generic wrapper class called **System.__ComObject**.</span></span>  
  
## <a name="default-marshaling-for-delegates"></a><span data-ttu-id="9a918-158">Маршалинг по умолчанию для делегатов</span><span class="sxs-lookup"><span data-stu-id="9a918-158">Default marshaling for delegates</span></span>  
 <span data-ttu-id="9a918-159">Управляемый делегат маршалируется как COM-интерфейс или как указатель на функцию на основе описанного ниже механизма вызовов.</span><span class="sxs-lookup"><span data-stu-id="9a918-159">A managed delegate is marshaled as a COM interface or as a function pointer, based on the calling mechanism:</span></span>  
  
- <span data-ttu-id="9a918-160">Для вызова неуправляемого кода делегат по умолчанию маршалируется как указатель на функцию.</span><span class="sxs-lookup"><span data-stu-id="9a918-160">For platform invoke, a delegate is marshaled as an unmanaged function pointer by default.</span></span>  
  
- <span data-ttu-id="9a918-161">Для COM-взаимодействия делегат по умолчанию маршалируется как COM-интерфейс типа **_Delegate**.</span><span class="sxs-lookup"><span data-stu-id="9a918-161">For COM interop, a delegate is marshaled as a COM interface of type **_Delegate** by default.</span></span> <span data-ttu-id="9a918-162">Интерфейс **_Delegate** определяется в библиотеке типов Mscorlib.tlb и содержит метод <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType>, который позволяет вызывать метод, на который ссылается делегат.</span><span class="sxs-lookup"><span data-stu-id="9a918-162">The **_Delegate** interface is defined in the Mscorlib.tlb type library and contains the <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> method, which enables you to call the method that the delegate references.</span></span>  
  
 <span data-ttu-id="9a918-163">В таблице ниже показаны варианты маршалинга для типа данных управляемого делегата.</span><span class="sxs-lookup"><span data-stu-id="9a918-163">The following table shows the marshaling options for the managed delegate data type.</span></span> <span data-ttu-id="9a918-164">Атрибут <xref:System.Runtime.InteropServices.MarshalAsAttribute> предоставляет несколько значений перечисления <xref:System.Runtime.InteropServices.UnmanagedType> для маршалинга делегатов.</span><span class="sxs-lookup"><span data-stu-id="9a918-164">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal delegates.</span></span>  
  
|<span data-ttu-id="9a918-165">Тип перечисления</span><span class="sxs-lookup"><span data-stu-id="9a918-165">Enumeration type</span></span>|<span data-ttu-id="9a918-166">Описание неуправляемого формата</span><span class="sxs-lookup"><span data-stu-id="9a918-166">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|<span data-ttu-id="9a918-167">**UnmanagedType.FunctionPtr**</span><span class="sxs-lookup"><span data-stu-id="9a918-167">**UnmanagedType.FunctionPtr**</span></span>|<span data-ttu-id="9a918-168">Указатель на неуправляемую функцию.</span><span class="sxs-lookup"><span data-stu-id="9a918-168">An unmanaged function pointer.</span></span>|  
|<span data-ttu-id="9a918-169">**UnmanagedType.Interface**</span><span class="sxs-lookup"><span data-stu-id="9a918-169">**UnmanagedType.Interface**</span></span>|<span data-ttu-id="9a918-170">Интерфейс типа **_Delegate**, как определено в Mscorlib.tlb.</span><span class="sxs-lookup"><span data-stu-id="9a918-170">An interface of type **_Delegate**, as defined in Mscorlib.tlb.</span></span>|  
  
 <span data-ttu-id="9a918-171">Рассмотрим пример кода, в котором методы `DelegateTestInterface` экспортируются в библиотеку типов COM.</span><span class="sxs-lookup"><span data-stu-id="9a918-171">Consider the following example code in which the methods of `DelegateTestInterface` are exported to a COM type library.</span></span> <span data-ttu-id="9a918-172">Обратите внимание на то, что только делегаты, помеченные ключевым словом **ref** (или **ByRef**), передаются как параметры In/Out.</span><span class="sxs-lookup"><span data-stu-id="9a918-172">Notice that only delegates marked with the **ref** (or **ByRef**) keyword are passed as In/Out parameters.</span></span>  
  
```csharp  
using System;  
using System.Runtime.InteropServices;  
  
public interface DelegateTest {  
void m1(Delegate d);  
void m2([MarshalAs(UnmanagedType.Interface)] Delegate d);     
void m3([MarshalAs(UnmanagedType.Interface)] ref Delegate d);    
void m4([MarshalAs(UnmanagedType.FunctionPtr)] Delegate d);   
void m5([MarshalAs(UnmanagedType.FunctionPtr)] ref Delegate d);     
}  
```  
  
### <a name="type-library-representation"></a><span data-ttu-id="9a918-173">Представление библиотеки типов</span><span class="sxs-lookup"><span data-stu-id="9a918-173">Type library representation</span></span>  
  
```cpp  
importlib("mscorlib.tlb");  
interface DelegateTest : IDispatch {  
[id(…)] HRESULT m1([in] _Delegate* d);  
[id(…)] HRESULT m2([in] _Delegate* d);  
[id(…)] HRESULT m3([in, out] _Delegate** d);  
[id()] HRESULT m4([in] int d);  
[id()] HRESULT m5([in, out] int *d);  
   };  
```  
  
 <span data-ttu-id="9a918-174">Указатель на функцию может быть разыменован, так же как и любой другой указатель на неуправляемую функцию.</span><span class="sxs-lookup"><span data-stu-id="9a918-174">A function pointer can be dereferenced, just as any other unmanaged function pointer can be dereferenced.</span></span>  

<span data-ttu-id="9a918-175">В этом примере при маршалировании двух делегатов в качестве <xref:System.Runtime.InteropServices.UnmanagedType.FunctionPtr?displayProperty=nameWithType> будет получен результат `int` и указатель на `int`.</span><span class="sxs-lookup"><span data-stu-id="9a918-175">In this example, when the two delegates are marshaled as <xref:System.Runtime.InteropServices.UnmanagedType.FunctionPtr?displayProperty=nameWithType>, the result is an `int` and a pointer to an `int`.</span></span> <span data-ttu-id="9a918-176">Поскольку типы делегатов маршалируются, `int` здесь представляет указатель на void (`void*`), то есть адрес делегата в памяти.</span><span class="sxs-lookup"><span data-stu-id="9a918-176">Because delegate types are being marshaled, `int` here represents a pointer to a void (`void*`), which is the address of the delegate in memory.</span></span> <span data-ttu-id="9a918-177">Другими словами, этот результат относится к 32-разрядным системам Windows, поскольку `int` здесь представляет размер указателя на функцию.</span><span class="sxs-lookup"><span data-stu-id="9a918-177">In other words, this result is specific to 32-bit Windows systems, since `int` here represents the size of the function pointer.</span></span>

> [!NOTE]
>  <span data-ttu-id="9a918-178">Ссылка на указатель на функцию в управляемом делегате, хранимая в неуправляемом коде, не препятствует выполнению средой CLR сборки мусора для управляемого объекта.</span><span class="sxs-lookup"><span data-stu-id="9a918-178">A reference to the function pointer to a managed delegate held by unmanaged code does not prevent the common language runtime from performing garbage collection on the managed object.</span></span>  
  
 <span data-ttu-id="9a918-179">Например, приведенный ниже код некорректен, так как ссылка на объект `cb`, передаваемая методу `SetChangeHandler`, не сохраняет объект `cb` в активном состоянии по окончании времени существования метода `Test`.</span><span class="sxs-lookup"><span data-stu-id="9a918-179">For example, the following code is incorrect because the reference to the `cb` object, passed to the `SetChangeHandler` method, does not keep `cb` alive beyond the life of the `Test` method.</span></span> <span data-ttu-id="9a918-180">После применения к объекту `cb` процедуры сборки мусора указатель на функцию, переданный в `SetChangeHandler`, становится недействительным.</span><span class="sxs-lookup"><span data-stu-id="9a918-180">Once the `cb` object is garbage collected, the function pointer passed to `SetChangeHandler` is no longer valid.</span></span>  
  
```csharp  
public class ExternalAPI {  
   [DllImport("External.dll")]  
   public static extern void SetChangeHandler(  
      [MarshalAs(UnmanagedType.FunctionPtr)]ChangeDelegate d);  
}  
public delegate bool ChangeDelegate([MarshalAs(UnmanagedType.LPWStr) string S);  
public class CallBackClass {  
   public bool OnChange(string S){ return true;}  
}  
internal class DelegateTest {  
   public static void Test() {  
      CallBackClass cb = new CallBackClass();  
      // Caution: The following reference on the cb object does not keep the   
      // object from being garbage collected after the Main method   
      // executes.  
      ExternalAPI.SetChangeHandler(new ChangeDelegate(cb.OnChange));     
   }  
}  
```  
  
 <span data-ttu-id="9a918-181">Чтобы компенсировать неожиданную сборку мусора, вызывающий объект должен гарантировать, что объект `cb` будет находиться в активном состоянии до тех пор, пока используется указатель на неуправляемую функцию.</span><span class="sxs-lookup"><span data-stu-id="9a918-181">To compensate for unexpected garbage collection, the caller must ensure that the `cb` object is kept alive as long as the unmanaged function pointer is in use.</span></span> <span data-ttu-id="9a918-182">Как показано в примере ниже, при необходимости можно настроить передачу уведомлений от неуправляемого кода в управляемый о том, что указатель на функцию больше не нужен.</span><span class="sxs-lookup"><span data-stu-id="9a918-182">Optionally, you can have the unmanaged code notify the managed code when the function pointer is no longer needed, as the following example shows.</span></span>  
  
```csharp  
internal class DelegateTest {  
   CallBackClass cb;  
   // Called before ever using the callback function.  
   public static void SetChangeHandler() {  
      cb = new CallBackClass();  
      ExternalAPI.SetChangeHandler(new ChangeDelegate(cb.OnChange));  
   }  
   // Called after using the callback function for the last time.  
   public static void RemoveChangeHandler() {  
      // The cb object can be collected now. The unmanaged code is   
      // finished with the callback function.  
      cb = null;  
   }  
}  
```  
  
## <a name="default-marshaling-for-value-types"></a><span data-ttu-id="9a918-183">Маршалинг по умолчанию для типов значений</span><span class="sxs-lookup"><span data-stu-id="9a918-183">Default marshaling for value types</span></span>  
 <span data-ttu-id="9a918-184">Большинство типов значений, такие как целые числа и числа с плавающей запятой, являются [непреобразуемыми](blittable-and-non-blittable-types.md) и не требуют маршалинга.</span><span class="sxs-lookup"><span data-stu-id="9a918-184">Most value types, such as integers and floating-point numbers, are [blittable](blittable-and-non-blittable-types.md) and do not require marshaling.</span></span> <span data-ttu-id="9a918-185">[Преобразуемые](blittable-and-non-blittable-types.md) типы представлены в управляемой и неуправляемой памяти по-разному и требуют маршалинга.</span><span class="sxs-lookup"><span data-stu-id="9a918-185">Other [non-blittable](blittable-and-non-blittable-types.md) types have dissimilar representations in managed and unmanaged memory and do require marshaling.</span></span> <span data-ttu-id="9a918-186">Другие типы требуют явного форматирования при пересечении границы взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="9a918-186">Still other types require explicit formatting across the interoperation boundary.</span></span>  
  
 <span data-ttu-id="9a918-187">В этом разделе представлены сведения о следующих форматированных типах значений:</span><span class="sxs-lookup"><span data-stu-id="9a918-187">This section provides information on the following formatted value types:</span></span>  
  
- [<span data-ttu-id="9a918-188">Типы значений, используемые в вызове неуправляемого кода</span><span class="sxs-lookup"><span data-stu-id="9a918-188">Value Types Used in Platform Invoke</span></span>](#value-types-used-in-platform-invoke)  
  
- [<span data-ttu-id="9a918-189">Типы значений, используемые в COM-взаимодействии</span><span class="sxs-lookup"><span data-stu-id="9a918-189">Value Types Used in COM Interop</span></span>](#value-types-used-in-com-interop)  
  
 <span data-ttu-id="9a918-190">Кроме описания форматированных типов, в этом разделе определяются [системные типы значений](#system-value-types), имеющие нестандартное поведение маршалинга.</span><span class="sxs-lookup"><span data-stu-id="9a918-190">In addition to describing formatted types, this topic identifies [System Value Types](#system-value-types) that have unusual marshaling behavior.</span></span>  
  
 <span data-ttu-id="9a918-191">Форматированный тип — это сложный тип, который содержит информацию, явным образом определяющую размещение его членов в памяти.</span><span class="sxs-lookup"><span data-stu-id="9a918-191">A formatted type is a complex type that contains information that explicitly controls the layout of its members in memory.</span></span> <span data-ttu-id="9a918-192">Сведения о размещении членов предоставляются с помощью атрибута <xref:System.Runtime.InteropServices.StructLayoutAttribute>.</span><span class="sxs-lookup"><span data-stu-id="9a918-192">The member layout information is provided using the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute.</span></span> <span data-ttu-id="9a918-193">Размещение может принимать одно из указанных ниже значений перечисления <xref:System.Runtime.InteropServices.LayoutKind>.</span><span class="sxs-lookup"><span data-stu-id="9a918-193">The layout can be one of the following <xref:System.Runtime.InteropServices.LayoutKind> enumeration values:</span></span>  
  
- <span data-ttu-id="9a918-194">**LayoutKind.Automatic**</span><span class="sxs-lookup"><span data-stu-id="9a918-194">**LayoutKind.Automatic**</span></span>  
  
     <span data-ttu-id="9a918-195">Указывает, что среда CLR для повышения эффективности может свободно изменять порядок членов типа.</span><span class="sxs-lookup"><span data-stu-id="9a918-195">Indicates that the common language runtime is free to reorder the members of the type for efficiency.</span></span> <span data-ttu-id="9a918-196">Тем не менее, когда тип значения передается в неуправляемый код, размещение членов является предсказуемым.</span><span class="sxs-lookup"><span data-stu-id="9a918-196">However, when a value type is passed to unmanaged code, the layout of the members is predictable.</span></span> <span data-ttu-id="9a918-197">При попытке маршалинга такой структуры автоматически вызывается исключение.</span><span class="sxs-lookup"><span data-stu-id="9a918-197">An attempt to marshal such a structure automatically causes an exception.</span></span>  
  
- <span data-ttu-id="9a918-198">**LayoutKind.Sequential**</span><span class="sxs-lookup"><span data-stu-id="9a918-198">**LayoutKind.Sequential**</span></span>  
  
     <span data-ttu-id="9a918-199">Указывает, что члены типа должны размещаться в неуправляемой памяти в том же порядке, в котором они появляются в определении управляемого типа.</span><span class="sxs-lookup"><span data-stu-id="9a918-199">Indicates that the members of the type are to be laid out in unmanaged memory in the same order in which they appear in the managed type definition.</span></span>  
  
- <span data-ttu-id="9a918-200">**LayoutKind.Explicit**</span><span class="sxs-lookup"><span data-stu-id="9a918-200">**LayoutKind.Explicit**</span></span>  
  
     <span data-ttu-id="9a918-201">Указывает, что члены располагаются в соответствии с атрибутом <xref:System.Runtime.InteropServices.FieldOffsetAttribute>, предоставляемым с каждым полем.</span><span class="sxs-lookup"><span data-stu-id="9a918-201">Indicates that the members are laid out according to the <xref:System.Runtime.InteropServices.FieldOffsetAttribute> supplied with each field.</span></span>  
  
### <a name="value-types-used-in-platform-invoke"></a><span data-ttu-id="9a918-202">Типы значений, используемые в вызове неуправляемого кода</span><span class="sxs-lookup"><span data-stu-id="9a918-202">Value Types Used in Platform Invoke</span></span>  
 <span data-ttu-id="9a918-203">В примере ниже типы `Point` и `Rect` предоставляют сведения о размещении членов с помощью атрибута **StructLayoutAttribute**.</span><span class="sxs-lookup"><span data-stu-id="9a918-203">In the following example the `Point` and `Rect` types provide member layout information using the **StructLayoutAttribute**.</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
<StructLayout(LayoutKind.Sequential)> Public Structure Point  
   Public x As Integer  
   Public y As Integer  
End Structure  
<StructLayout(LayoutKind.Explicit)> Public Structure Rect  
   <FieldOffset(0)> Public left As Integer  
   <FieldOffset(4)> Public top As Integer  
   <FieldOffset(8)> Public right As Integer  
   <FieldOffset(12)> Public bottom As Integer  
End Structure  
```  
  
```csharp  
using System.Runtime.InteropServices;  
[StructLayout(LayoutKind.Sequential)]  
public struct Point {  
   public int x;  
   public int y;  
}     
  
[StructLayout(LayoutKind.Explicit)]  
public struct Rect {  
   [FieldOffset(0)] public int left;  
   [FieldOffset(4)] public int top;  
   [FieldOffset(8)] public int right;  
   [FieldOffset(12)] public int bottom;  
}  
```  
  
 <span data-ttu-id="9a918-204">При маршалинге в неуправляемый код эти форматированные типы маршалируются как структуры стиля C.</span><span class="sxs-lookup"><span data-stu-id="9a918-204">When marshaled to unmanaged code, these formatted types are marshaled as C-style structures.</span></span> <span data-ttu-id="9a918-205">Это обеспечивает простой способ вызова неуправляемого интерфейса API с аргументами в виде структур.</span><span class="sxs-lookup"><span data-stu-id="9a918-205">This provides an easy way of calling an unmanaged API that has structure arguments.</span></span> <span data-ttu-id="9a918-206">Например, структуры `POINT` и `RECT` могут передаваться в функцию **PtInRect** Microsoft Windows API следующим образом:</span><span class="sxs-lookup"><span data-stu-id="9a918-206">For example, the `POINT` and `RECT` structures can be passed to the Microsoft Windows API **PtInRect** function as follows:</span></span>  
  
```cpp  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 <span data-ttu-id="9a918-207">Вы можете передать структуры с помощью следующего определения вызова неуправляемого кода:</span><span class="sxs-lookup"><span data-stu-id="9a918-207">You can pass structures using the following platform invoke definition:</span></span>  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function PtInRect Lib "User32.dll" (
        ByRef r As Rect, p As Point) As Boolean
End Class
```
  
```csharp
internal static class NativeMethods
{
   [DllImport("User32.dll")]
   internal static extern bool PtInRect(ref Rect r, Point p);
}
```
  
 <span data-ttu-id="9a918-208">Тип значения `Rect` должен передаваться по ссылке, потому что неуправляемый интерфейс API ожидает, что в функцию будет передан указатель на `RECT`.</span><span class="sxs-lookup"><span data-stu-id="9a918-208">The `Rect` value type must be passed by reference because the unmanaged API is expecting a pointer to a `RECT` to be passed to the function.</span></span> <span data-ttu-id="9a918-209">Тип значения `Point` передается по значению, так как неуправляемый интерфейс API ожидает, что `POINT` будет передан в стек.</span><span class="sxs-lookup"><span data-stu-id="9a918-209">The `Point` value type is passed by value because the unmanaged API expects the `POINT` to be passed on the stack.</span></span> <span data-ttu-id="9a918-210">Это небольшое различие очень важно.</span><span class="sxs-lookup"><span data-stu-id="9a918-210">This subtle difference is very important.</span></span> <span data-ttu-id="9a918-211">Ссылки передаются в неуправляемый код как указатели.</span><span class="sxs-lookup"><span data-stu-id="9a918-211">References are passed to unmanaged code as pointers.</span></span> <span data-ttu-id="9a918-212">Значения передаются в неуправляемый код в стеке.</span><span class="sxs-lookup"><span data-stu-id="9a918-212">Values are passed to unmanaged code on the stack.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9a918-213">При маршалинге форматированного типа в виде структуры доступны только поля внутри этого типа.</span><span class="sxs-lookup"><span data-stu-id="9a918-213">When a formatted type is marshaled as a structure, only the fields within the type are accessible.</span></span> <span data-ttu-id="9a918-214">Если у типа есть методы, свойства или события, то они недоступны из неуправляемого кода.</span><span class="sxs-lookup"><span data-stu-id="9a918-214">If the type has methods, properties, or events, they are inaccessible from unmanaged code.</span></span>  
  
 <span data-ttu-id="9a918-215">Классы тоже можно маршалировать в неуправляемый код как структуры стиля языка С при условии, что они имеют фиксированное размещение членов.</span><span class="sxs-lookup"><span data-stu-id="9a918-215">Classes can also be marshaled to unmanaged code as C-style structures, provided they have fixed member layout.</span></span> <span data-ttu-id="9a918-216">Сведения о размещении членов класса также предоставляются с помощью атрибута <xref:System.Runtime.InteropServices.StructLayoutAttribute>.</span><span class="sxs-lookup"><span data-stu-id="9a918-216">The member layout information for a class is also provided with the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute.</span></span> <span data-ttu-id="9a918-217">Основное различие между типами значений с фиксированным размещением и классами с фиксированным размещением заключает в способе маршалинга в неуправляемый код.</span><span class="sxs-lookup"><span data-stu-id="9a918-217">The main difference between value types with fixed layout and classes with fixed layout is the way in which they are marshaled to unmanaged code.</span></span> <span data-ttu-id="9a918-218">Типы значений передаются по значению (в стеке), поэтому любые изменения, внесенные в члены этого типа вызываемым объектом, не видны вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="9a918-218">Value types are passed by value (on the stack) and consequently any changes made to the members of the type by the callee are not seen by the caller.</span></span> <span data-ttu-id="9a918-219">Ссылочные типы передаются по ссылке (ссылка на тип передается в стеке). Поэтому все изменения, внесенные в члены непреобразуемого типа вызываемым объектом, видны вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="9a918-219">Reference types are passed by reference (a reference to the type is passed on the stack); consequently, all changes made to blittable-type members of a type by the callee are seen by the caller.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9a918-220">Если ссылочный тип содержит члены преобразуемого типа, преобразование должно выполняться дважды: первый раз — при передаче аргумента неуправляемой стороне, а второй раз — при возврате из вызова.</span><span class="sxs-lookup"><span data-stu-id="9a918-220">If a reference type has members of non-blittable types, conversion is required twice: the first time when an argument is passed to the unmanaged side and the second time on return from the call.</span></span> <span data-ttu-id="9a918-221">В связи с появлением дополнительных издержек параметры In/Out необходимо применять к аргументу в явном виде, если вызывающий объект должен учитывать изменения, внесенные вызываемым объектом.</span><span class="sxs-lookup"><span data-stu-id="9a918-221">Due to this added overhead, In/Out parameters must be explicitly applied to an argument if the caller wants to see changes made by the callee.</span></span>  
  
 <span data-ttu-id="9a918-222">В примере ниже класс `SystemTime` имеет последовательное размещение членов и может быть передан в функцию **GetSystemTime** API Windows.</span><span class="sxs-lookup"><span data-stu-id="9a918-222">In the following example, the `SystemTime` class has sequential member layout and can be passed to the Windows API **GetSystemTime** function.</span></span>  
  
```vb  
<StructLayout(LayoutKind.Sequential)> Public Class SystemTime  
   Public wYear As System.UInt16  
   Public wMonth As System.UInt16  
   Public wDayOfWeek As System.UInt16  
   Public wDay As System.UInt16  
   Public wHour As System.UInt16  
   Public wMinute As System.UInt16  
   Public wSecond As System.UInt16  
   Public wMilliseconds As System.UInt16  
End Class  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
   public class SystemTime {  
   public ushort wYear;   
   public ushort wMonth;  
   public ushort wDayOfWeek;   
   public ushort wDay;   
   public ushort wHour;   
   public ushort wMinute;   
   public ushort wSecond;   
   public ushort wMilliseconds;   
}  
```  
  
 <span data-ttu-id="9a918-223">Функция **GetSystemTime** определяется следующим образом:</span><span class="sxs-lookup"><span data-stu-id="9a918-223">The **GetSystemTime** function is defined as follows:</span></span>  
  
```cpp  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 <span data-ttu-id="9a918-224">Эквивалентное определение вызова неуправляемого кода **GetSystemTime** выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="9a918-224">The equivalent platform invoke definition for **GetSystemTime** is as follows:</span></span>  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Sub GetSystemTime Lib "Kernel32.dll" (
        ByVal sysTime As SystemTime)
End Class
```
  
```csharp
internal static class NativeMethods
{
   [DllImport("Kernel32.dll", CharSet = CharSet.Auto)]
   internal static extern void GetSystemTime(SystemTime st);
}
```
  
 <span data-ttu-id="9a918-225">Обратите внимание на то, что аргумент `SystemTime` не типизирован как ссылочный аргумент, потому что `SystemTime` — это класс, а не тип значения.</span><span class="sxs-lookup"><span data-stu-id="9a918-225">Notice that the `SystemTime` argument is not typed as a reference argument because `SystemTime` is a class, not a value type.</span></span> <span data-ttu-id="9a918-226">В отличие от типов значений, классы всегда передаются по ссылке.</span><span class="sxs-lookup"><span data-stu-id="9a918-226">Unlike value types, classes are always passed by reference.</span></span>  
  
 <span data-ttu-id="9a918-227">В примере кода ниже показан другой класс `Point`, который содержит метод с именем `SetXY`.</span><span class="sxs-lookup"><span data-stu-id="9a918-227">The following code example shows a different `Point` class that has a method called `SetXY`.</span></span> <span data-ttu-id="9a918-228">Так как этот тип имеет последовательную компоновку, он может быть передан в неуправляемый код и маршалирован как структура.</span><span class="sxs-lookup"><span data-stu-id="9a918-228">Because the type has sequential layout, it can be passed to unmanaged code and marshaled as a structure.</span></span> <span data-ttu-id="9a918-229">Однако член `SetXY` нельзя вызвать из неуправляемого кода, даже когда объект передается по ссылке.</span><span class="sxs-lookup"><span data-stu-id="9a918-229">However, the `SetXY` member is not callable from unmanaged code, even though the object is passed by reference.</span></span>  
  
```vb  
<StructLayout(LayoutKind.Sequential)> Public Class Point  
   Private x, y As Integer  
   Public Sub SetXY(x As Integer, y As Integer)  
      Me.x = x  
      Me.y = y  
   End Sub  
End Class  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public class Point {  
   int x, y;  
   public void SetXY(int x, int y){   
      this.x = x;  
      this.y = y;  
   }  
}  
```  
  
### <a name="value-types-used-in-com-interop"></a><span data-ttu-id="9a918-230">Типы значений, используемые во COM-взаимодействии</span><span class="sxs-lookup"><span data-stu-id="9a918-230">Value Types Used in COM Interop</span></span>  
 <span data-ttu-id="9a918-231">Форматированные типы могут также передаваться в вызовы метода COM-взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="9a918-231">Formatted types can also be passed to COM interop method calls.</span></span> <span data-ttu-id="9a918-232">Фактически при экспорте в библиотеку типов типы значений автоматически преобразуются в структуры.</span><span class="sxs-lookup"><span data-stu-id="9a918-232">In fact, when exported to a type library, value types are automatically converted to structures.</span></span> <span data-ttu-id="9a918-233">Как показано в примере ниже, тип значения `Point` становится определением типа (typedef) с именем `Point`.</span><span class="sxs-lookup"><span data-stu-id="9a918-233">As the following example shows, the `Point` value type becomes a type definition (typedef) with the name `Point`.</span></span> <span data-ttu-id="9a918-234">Все ссылки на тип значения `Point` в любом другом месте библиотеки типов заменяются на определение типа typedef `Point`.</span><span class="sxs-lookup"><span data-stu-id="9a918-234">All references to the `Point` value type elsewhere in the type library are replaced with the `Point` typedef.</span></span>  
  
 <span data-ttu-id="9a918-235">**Представление библиотеки типов**</span><span class="sxs-lookup"><span data-stu-id="9a918-235">**Type library representation**</span></span>  
  
```cpp  
typedef struct tagPoint {  
   int x;  
   int y;  
} Point;  
interface _Graphics {  
   …  
   HRESULT SetPoint ([in] Point p)  
   HRESULT SetPointRef ([in,out] Point *p)  
   HRESULT GetPoint ([out,retval] Point *p)  
}  
```  
  
 <span data-ttu-id="9a918-236">Те же самые правила, которые используются для маршалинга значений и ссылок в вызовы неуправляемого кода, применяются и при маршалинге через COM-интерфейсы.</span><span class="sxs-lookup"><span data-stu-id="9a918-236">The same rules used to marshal values and references to platform invoke calls are used when marshaling through COM interfaces.</span></span> <span data-ttu-id="9a918-237">Например, когда экземпляр типа значения `Point` передается из .NET Framework в COM, `Point` передается по значению.</span><span class="sxs-lookup"><span data-stu-id="9a918-237">For example, when an instance of the `Point` value type is passed from the .NET Framework to COM, the `Point` is passed by value.</span></span> <span data-ttu-id="9a918-238">Если тип значения `Point` передается по ссылке, указатель на `Point` передается в стеке.</span><span class="sxs-lookup"><span data-stu-id="9a918-238">If the `Point` value type is passed by reference, a pointer to a `Point` is passed on the stack.</span></span> <span data-ttu-id="9a918-239">Упаковщик взаимодействия не поддерживает более высокие уровни косвенного обращения (**Point** \*\*) в любом направлении.</span><span class="sxs-lookup"><span data-stu-id="9a918-239">The interop marshaler does not support higher levels of indirection (**Point** \*\*) in either direction.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9a918-240">Структуры, для которых значение перечисления <xref:System.Runtime.InteropServices.LayoutKind> установлено равным **Explicit**, не могут использоваться в COM-взаимодействии, так как экспортированная библиотека типов не может представлять явное размещение.</span><span class="sxs-lookup"><span data-stu-id="9a918-240">Structures having the <xref:System.Runtime.InteropServices.LayoutKind> enumeration value set to **Explicit** cannot be used in COM interop because the exported type library cannot express an explicit layout.</span></span>  
  
### <a name="system-value-types"></a><span data-ttu-id="9a918-241">Системные типы значений</span><span class="sxs-lookup"><span data-stu-id="9a918-241">System Value Types</span></span>  
 <span data-ttu-id="9a918-242">Пространство имен <xref:System> содержит несколько типов значений, представляющих собой упакованную форму простых типов среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="9a918-242">The <xref:System> namespace has several value types that represent the boxed form of the runtime primitive types.</span></span> <span data-ttu-id="9a918-243">Например, структура типов значений <xref:System.Int32?displayProperty=nameWithType> представляет собой упакованную форму **ELEMENT_TYPE_I4**.</span><span class="sxs-lookup"><span data-stu-id="9a918-243">For example, the value type <xref:System.Int32?displayProperty=nameWithType> structure represents the boxed form of **ELEMENT_TYPE_I4**.</span></span> <span data-ttu-id="9a918-244">Вместо маршалинга этих типов в качестве структур, как в случае с другими форматированными типами, их следует маршалировать так же, как и соответствующие простые типы.</span><span class="sxs-lookup"><span data-stu-id="9a918-244">Instead of marshaling these types as structures, as other formatted types are, you marshal them in the same way as the primitive types they box.</span></span> <span data-ttu-id="9a918-245">Соответственно, **System.Int32** маршалируется как **ELEMENT_TYPE_I4**, а не как структура, содержащая один член типа **long**.</span><span class="sxs-lookup"><span data-stu-id="9a918-245">**System.Int32** is therefore marshaled as **ELEMENT_TYPE_I4** instead of as a structure containing a single member of type **long**.</span></span> <span data-ttu-id="9a918-246">В таблице ниже приведен список типов значений в пространстве имен **System**, являющихся упакованными представлениями простых типов.</span><span class="sxs-lookup"><span data-stu-id="9a918-246">The following table contains a list of the value types in the **System** namespace that are boxed representations of primitive types.</span></span>  
  
|<span data-ttu-id="9a918-247">Системный тип значения</span><span class="sxs-lookup"><span data-stu-id="9a918-247">System value type</span></span>|<span data-ttu-id="9a918-248">Тип элемента</span><span class="sxs-lookup"><span data-stu-id="9a918-248">Element type</span></span>|  
|-----------------------|------------------|  
|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="9a918-249">**ELEMENT_TYPE_BOOLEAN**</span><span class="sxs-lookup"><span data-stu-id="9a918-249">**ELEMENT_TYPE_BOOLEAN**</span></span>|  
|<xref:System.SByte?displayProperty=nameWithType>|<span data-ttu-id="9a918-250">**ELEMENT_TYPE_I1**</span><span class="sxs-lookup"><span data-stu-id="9a918-250">**ELEMENT_TYPE_I1**</span></span>|  
|<xref:System.Byte?displayProperty=nameWithType>|<span data-ttu-id="9a918-251">**ELEMENT_TYPE_UI1**</span><span class="sxs-lookup"><span data-stu-id="9a918-251">**ELEMENT_TYPE_UI1**</span></span>|  
|<xref:System.Char?displayProperty=nameWithType>|<span data-ttu-id="9a918-252">**ELEMENT_TYPE_CHAR**</span><span class="sxs-lookup"><span data-stu-id="9a918-252">**ELEMENT_TYPE_CHAR**</span></span>|  
|<xref:System.Int16?displayProperty=nameWithType>|<span data-ttu-id="9a918-253">**ELEMENT_TYPE_I2**</span><span class="sxs-lookup"><span data-stu-id="9a918-253">**ELEMENT_TYPE_I2**</span></span>|  
|<xref:System.UInt16?displayProperty=nameWithType>|<span data-ttu-id="9a918-254">**ELEMENT_TYPE_U2**</span><span class="sxs-lookup"><span data-stu-id="9a918-254">**ELEMENT_TYPE_U2**</span></span>|  
|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="9a918-255">**ELEMENT_TYPE_I4**</span><span class="sxs-lookup"><span data-stu-id="9a918-255">**ELEMENT_TYPE_I4**</span></span>|  
|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="9a918-256">**ELEMENT_TYPE_U4**</span><span class="sxs-lookup"><span data-stu-id="9a918-256">**ELEMENT_TYPE_U4**</span></span>|  
|<xref:System.Int64?displayProperty=nameWithType>|<span data-ttu-id="9a918-257">**ELEMENT_TYPE_I8**</span><span class="sxs-lookup"><span data-stu-id="9a918-257">**ELEMENT_TYPE_I8**</span></span>|  
|<xref:System.UInt64?displayProperty=nameWithType>|<span data-ttu-id="9a918-258">**ELEMENT_TYPE_U8**</span><span class="sxs-lookup"><span data-stu-id="9a918-258">**ELEMENT_TYPE_U8**</span></span>|  
|<xref:System.Single?displayProperty=nameWithType>|<span data-ttu-id="9a918-259">**ELEMENT_TYPE_R4**</span><span class="sxs-lookup"><span data-stu-id="9a918-259">**ELEMENT_TYPE_R4**</span></span>|  
|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="9a918-260">**ELEMENT_TYPE_R8**</span><span class="sxs-lookup"><span data-stu-id="9a918-260">**ELEMENT_TYPE_R8**</span></span>|  
|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="9a918-261">**ELEMENT_TYPE_STRING**</span><span class="sxs-lookup"><span data-stu-id="9a918-261">**ELEMENT_TYPE_STRING**</span></span>|  
|<xref:System.IntPtr?displayProperty=nameWithType>|<span data-ttu-id="9a918-262">**ELEMENT_TYPE_I**</span><span class="sxs-lookup"><span data-stu-id="9a918-262">**ELEMENT_TYPE_I**</span></span>|  
|<xref:System.UIntPtr?displayProperty=nameWithType>|<span data-ttu-id="9a918-263">**ELEMENT_TYPE_U**</span><span class="sxs-lookup"><span data-stu-id="9a918-263">**ELEMENT_TYPE_U**</span></span>|  
  
 <span data-ttu-id="9a918-264">Некоторые типы значений в пространстве имен **System** обрабатываются по-другому.</span><span class="sxs-lookup"><span data-stu-id="9a918-264">Some other value types in the **System** namespace are handled differently.</span></span> <span data-ttu-id="9a918-265">Так как неуправляемый код уже имеет хорошо определенные форматы для таких типов, у упаковщика есть специальные правила для их маршалинга.</span><span class="sxs-lookup"><span data-stu-id="9a918-265">Because the unmanaged code already has well-established formats for these types, the marshaler has special rules for marshaling them.</span></span> <span data-ttu-id="9a918-266">В таблице ниже представлен список этих специальных типов значений в пространстве имен **System**, а также неуправляемых типов, в которые они маршалируются.</span><span class="sxs-lookup"><span data-stu-id="9a918-266">The following table lists the special value types in the **System** namespace, as well as the unmanaged type they are marshaled to.</span></span>  
  
|<span data-ttu-id="9a918-267">Системный тип значения</span><span class="sxs-lookup"><span data-stu-id="9a918-267">System value type</span></span>|<span data-ttu-id="9a918-268">Тип IDL</span><span class="sxs-lookup"><span data-stu-id="9a918-268">IDL type</span></span>|  
|-----------------------|--------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|<span data-ttu-id="9a918-269">**DATE**</span><span class="sxs-lookup"><span data-stu-id="9a918-269">**DATE**</span></span>|  
|<xref:System.Decimal?displayProperty=nameWithType>|<span data-ttu-id="9a918-270">**DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="9a918-270">**DECIMAL**</span></span>|  
|<xref:System.Guid?displayProperty=nameWithType>|<span data-ttu-id="9a918-271">**GUID**</span><span class="sxs-lookup"><span data-stu-id="9a918-271">**GUID**</span></span>|  
|<xref:System.Drawing.Color?displayProperty=nameWithType>|<span data-ttu-id="9a918-272">**OLE_COLOR**</span><span class="sxs-lookup"><span data-stu-id="9a918-272">**OLE_COLOR**</span></span>|  
  
 <span data-ttu-id="9a918-273">В приведенном ниже коде показано определение неуправляемых типов **DATE**, **GUID**, **DECIMAL** и **OLE_COLOR** в библиотеке типов Stdole2.</span><span class="sxs-lookup"><span data-stu-id="9a918-273">The following code shows the definition of the unmanaged types **DATE**, **GUID**, **DECIMAL**, and **OLE_COLOR** in the Stdole2 type library.</span></span>  
  
#### <a name="type-library-representation"></a><span data-ttu-id="9a918-274">Представление библиотеки типов</span><span class="sxs-lookup"><span data-stu-id="9a918-274">Type library representation</span></span>  
  
```cpp  
typedef double DATE;  
typedef DWORD OLE_COLOR;  
  
typedef struct tagDEC {  
    USHORT    wReserved;  
    BYTE      scale;  
    BYTE      sign;  
    ULONG     Hi32;  
    ULONGLONG Lo64;  
} DECIMAL;  
  
typedef struct tagGUID {  
    DWORD Data1;  
    WORD  Data2;  
    WORD  Data3;  
    BYTE  Data4[ 8 ];  
} GUID;  
```  
  
 <span data-ttu-id="9a918-275">В коде ниже показаны соответствующие определения в управляемом интерфейсе `IValueTypes`.</span><span class="sxs-lookup"><span data-stu-id="9a918-275">The following code shows the corresponding definitions in the managed `IValueTypes` interface.</span></span>  
  
```vb  
Public Interface IValueTypes  
   Sub M1(d As System.DateTime)  
   Sub M2(d As System.Guid)  
   Sub M3(d As System.Decimal)  
   Sub M4(d As System.Drawing.Color)  
End Interface  
```  
  
```csharp  
public interface IValueTypes {  
   void M1(System.DateTime d);  
   void M2(System.Guid d);  
   void M3(System.Decimal d);  
   void M4(System.Drawing.Color d);  
}  
```  
  
#### <a name="type-library-representation"></a><span data-ttu-id="9a918-276">Представление библиотеки типов</span><span class="sxs-lookup"><span data-stu-id="9a918-276">Type library representation</span></span>  
  
```cpp  
[…]  
interface IValueTypes : IDispatch {  
   HRESULT M1([in] DATE d);  
   HRESULT M2([in] GUID d);  
   HRESULT M3([in] DECIMAL d);  
   HRESULT M4([in] OLE_COLOR d);  
};  
```  
  
## <a name="see-also"></a><span data-ttu-id="9a918-277">См. также</span><span class="sxs-lookup"><span data-stu-id="9a918-277">See also</span></span>

- [<span data-ttu-id="9a918-278">Преобразуемые и непреобразуемые типы</span><span class="sxs-lookup"><span data-stu-id="9a918-278">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- [<span data-ttu-id="9a918-279">Копирование и закрепление</span><span class="sxs-lookup"><span data-stu-id="9a918-279">Copying and Pinning</span></span>](copying-and-pinning.md)
- [<span data-ttu-id="9a918-280">Маршалинг по умолчанию для массивов</span><span class="sxs-lookup"><span data-stu-id="9a918-280">Default Marshaling for Arrays</span></span>](default-marshaling-for-arrays.md)
- [<span data-ttu-id="9a918-281">Маршалинг по умолчанию для объектов</span><span class="sxs-lookup"><span data-stu-id="9a918-281">Default Marshaling for Objects</span></span>](default-marshaling-for-objects.md)
- [<span data-ttu-id="9a918-282">Маршалинг по умолчанию для строк</span><span class="sxs-lookup"><span data-stu-id="9a918-282">Default Marshaling for Strings</span></span>](default-marshaling-for-strings.md)
