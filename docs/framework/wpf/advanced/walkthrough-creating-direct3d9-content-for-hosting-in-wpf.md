---
title: Пошаговое руководство. Создание содержимого Direct3D9 для размещения в WPF
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- WPF [WPF], creating Direct3D9 content
- Direct3D9 [WPF interoperability], creating Direct3D9 content
ms.assetid: 286e98bc-1eaa-4b5e-923d-3490a9cca5fc
ms.openlocfilehash: 462220b526db90d3acfa90a28f9bfd56dbe813e2
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991396"
---
# <a name="walkthrough-creating-direct3d9-content-for-hosting-in-wpf"></a><span data-ttu-id="44234-102">Пошаговое руководство. Создание содержимого Direct3D9 для размещения в WPF</span><span class="sxs-lookup"><span data-stu-id="44234-102">Walkthrough: Creating Direct3D9 Content for Hosting in WPF</span></span>
<span data-ttu-id="44234-103">В этом пошаговом руководстве показано, как создать содержимое Direct3D9, которое подходит для размещения в приложении Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="44234-103">This walkthrough shows how to create Direct3D9 content that is suitable for hosting in a Windows Presentation Foundation (WPF) application.</span></span> <span data-ttu-id="44234-104">Дополнительные сведения о размещении содержимого Direct3D9 в приложениях WPF см. в разделе [взаимодействие WPF и Direct3D9](wpf-and-direct3d9-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="44234-104">For more information on hosting Direct3D9 content in WPF applications, see [WPF and Direct3D9 Interoperation](wpf-and-direct3d9-interoperation.md).</span></span>

 <span data-ttu-id="44234-105">В руководстве выполняются следующие задачи:</span><span class="sxs-lookup"><span data-stu-id="44234-105">In this walkthrough, you perform the following tasks:</span></span>

- <span data-ttu-id="44234-106">Создайте проект Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="44234-106">Create a Direct3D9 project.</span></span>

- <span data-ttu-id="44234-107">Настройка проекта Direct3D9 для размещения в приложении WPF.</span><span class="sxs-lookup"><span data-stu-id="44234-107">Configure the Direct3D9 project for hosting in a WPF application.</span></span>

 <span data-ttu-id="44234-108">По завершении у вас будет библиотека DLL, содержащая содержимое Direct3D9 для использования в приложении WPF.</span><span class="sxs-lookup"><span data-stu-id="44234-108">When you are finished, you will have a DLL that contains Direct3D9 content for use in a WPF application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="44234-109">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="44234-109">Prerequisites</span></span>
 <span data-ttu-id="44234-110">Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.</span><span class="sxs-lookup"><span data-stu-id="44234-110">You need the following components to complete this walkthrough:</span></span>

- <span data-ttu-id="44234-111">Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="44234-111">Visual Studio 2010.</span></span>

- <span data-ttu-id="44234-112">Пакет SDK для DirectX 9 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="44234-112">DirectX SDK 9 or later.</span></span>

## <a name="creating-the-direct3d9-project"></a><span data-ttu-id="44234-113">Создание проекта Direct3D9</span><span class="sxs-lookup"><span data-stu-id="44234-113">Creating the Direct3D9 Project</span></span>
 <span data-ttu-id="44234-114">Первым шагом является создание и Настройка проекта Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="44234-114">The first step is to create and configure the Direct3D9 project.</span></span>

#### <a name="to-create-the-direct3d9-project"></a><span data-ttu-id="44234-115">Создание проекта Direct3D9</span><span class="sxs-lookup"><span data-stu-id="44234-115">To create the Direct3D9 project</span></span>

1. <span data-ttu-id="44234-116">Создайте новый проект Win32 в C++ с именем `D3DContent`.</span><span class="sxs-lookup"><span data-stu-id="44234-116">Create a new Win32 Project in C++ named `D3DContent`.</span></span>

     <span data-ttu-id="44234-117">Откроется мастер приложений Win32 и отобразится экран приветствия.</span><span class="sxs-lookup"><span data-stu-id="44234-117">The Win32 Application Wizard opens and displays the Welcome screen.</span></span>

2. <span data-ttu-id="44234-118">Нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="44234-118">Click **Next**.</span></span>

     <span data-ttu-id="44234-119">Появится экран параметры приложения.</span><span class="sxs-lookup"><span data-stu-id="44234-119">The Application Settings screen appears.</span></span>

3. <span data-ttu-id="44234-120">В разделе **Application Type: (тип приложения** ) выберите параметр **DLL** .</span><span class="sxs-lookup"><span data-stu-id="44234-120">In the **Application type:** section, select the **DLL** option.</span></span>

4. <span data-ttu-id="44234-121">Нажмите кнопку **Готово**.</span><span class="sxs-lookup"><span data-stu-id="44234-121">Click **Finish**.</span></span>

     <span data-ttu-id="44234-122">Создается проект D3DContent.</span><span class="sxs-lookup"><span data-stu-id="44234-122">The D3DContent project is generated.</span></span>

5. <span data-ttu-id="44234-123">В обозреватель решений щелкните правой кнопкой мыши проект D3DContent и выберите пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="44234-123">In Solution Explorer, right-click the D3DContent project and select **Properties**.</span></span>

     <span data-ttu-id="44234-124">Откроется диалоговое окно **страницы свойств D3DContent** .</span><span class="sxs-lookup"><span data-stu-id="44234-124">The **D3DContent Property Pages** dialog box opens.</span></span>

6. <span data-ttu-id="44234-125">Выберите узел **C/C++**  .</span><span class="sxs-lookup"><span data-stu-id="44234-125">Select the **C/C++** node.</span></span>

7. <span data-ttu-id="44234-126">В поле **Дополнительные каталоги включаемых** данных укажите расположение папки с DirectX include.</span><span class="sxs-lookup"><span data-stu-id="44234-126">In the **Additional Include Directories** field, specify the location of the DirectX include folder.</span></span> <span data-ttu-id="44234-127">Расположение по умолчанию для этой папки —%ProgramFiles%\Microsoft DirectX SDK (*версия*) \инклуде.</span><span class="sxs-lookup"><span data-stu-id="44234-127">The default location for this folder is %ProgramFiles%\Microsoft DirectX SDK (*version*)\Include.</span></span>

8. <span data-ttu-id="44234-128">Дважды щелкните узел **компоновщика** , чтобы развернуть его.</span><span class="sxs-lookup"><span data-stu-id="44234-128">Double-click the **Linker** node to expand it.</span></span>

9. <span data-ttu-id="44234-129">В поле **Дополнительные каталоги библиотек** укажите расположение папки библиотеки DirectX.</span><span class="sxs-lookup"><span data-stu-id="44234-129">In the **Additional Library Directories** field, specify the location of the DirectX libraries folder.</span></span> <span data-ttu-id="44234-130">Расположение по умолчанию для этой папки —%ProgramFiles%\Microsoft DirectX SDK (*версия*) \Lib\x86.</span><span class="sxs-lookup"><span data-stu-id="44234-130">The default location for this folder is %ProgramFiles%\Microsoft DirectX SDK (*version*)\Lib\x86.</span></span>

10. <span data-ttu-id="44234-131">Выберите **входной** узел.</span><span class="sxs-lookup"><span data-stu-id="44234-131">Select the **Input** node.</span></span>

11. <span data-ttu-id="44234-132">В поле **Дополнительные зависимости** добавьте `d3d9.lib` файлы и `d3dx9.lib` .</span><span class="sxs-lookup"><span data-stu-id="44234-132">In the **Additional Dependencies** field, add the `d3d9.lib` and `d3dx9.lib` files.</span></span>

12. <span data-ttu-id="44234-133">В Обозреватель решений добавьте новый файл определения модуля (DEF) с именем `D3DContent.def` в проект.</span><span class="sxs-lookup"><span data-stu-id="44234-133">In Solution Explorer, add a new module definition file (.def) named `D3DContent.def` to the project.</span></span>

## <a name="creating-the-direct3d9-content"></a><span data-ttu-id="44234-134">Создание содержимого Direct3D9</span><span class="sxs-lookup"><span data-stu-id="44234-134">Creating the Direct3D9 Content</span></span>
 <span data-ttu-id="44234-135">Чтобы обеспечить максимальную производительность, содержимое Direct3D9 должно использовать определенные параметры.</span><span class="sxs-lookup"><span data-stu-id="44234-135">To get the best performance, your Direct3D9 content must use particular settings.</span></span> <span data-ttu-id="44234-136">В следующем коде показано, как создать поверхность Direct3D9 с лучшими характеристиками производительности.</span><span class="sxs-lookup"><span data-stu-id="44234-136">The following code shows how to create a Direct3D9 surface that has the best performance characteristics.</span></span> <span data-ttu-id="44234-137">Дополнительные сведения см. в разделе [вопросы производительности для совместимости с Direct3D9 и WPF](performance-considerations-for-direct3d9-and-wpf-interoperability.md).</span><span class="sxs-lookup"><span data-stu-id="44234-137">For more information, see [Performance Considerations for Direct3D9 and WPF Interoperability](performance-considerations-for-direct3d9-and-wpf-interoperability.md).</span></span>

#### <a name="to-create-the-direct3d9-content"></a><span data-ttu-id="44234-138">Создание содержимого Direct3D9</span><span class="sxs-lookup"><span data-stu-id="44234-138">To create the Direct3D9 content</span></span>

1. <span data-ttu-id="44234-139">С помощью обозреватель решений добавьте в C++ проект три класса с именем:</span><span class="sxs-lookup"><span data-stu-id="44234-139">Using Solution Explorer, add three C++ classes to the project named the following.</span></span>

     <span data-ttu-id="44234-140">`CRenderer`(с виртуальным деструктором)</span><span class="sxs-lookup"><span data-stu-id="44234-140">`CRenderer` (with virtual destructor)</span></span>

     `CRendererManager`

     `CTriangleRenderer`

2. <span data-ttu-id="44234-141">Откройте модуль подготовки отчетов. h в редакторе кода и замените автоматически созданный код следующим кодом.</span><span class="sxs-lookup"><span data-stu-id="44234-141">Open Renderer.h in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#RendererH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.h#rendererh)]

3. <span data-ttu-id="44234-142">Откройте модуль подготовки отчетов. cpp в редакторе кода и замените автоматически созданный код следующим кодом.</span><span class="sxs-lookup"><span data-stu-id="44234-142">Open Renderer.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#RendererCPP](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderercpp)]

4. <span data-ttu-id="44234-143">Откройте Рендерерманажер. h в редакторе кода и замените автоматически созданный код следующим кодом.</span><span class="sxs-lookup"><span data-stu-id="44234-143">Open RendererManager.h in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.h#renderermanagerh)]

5. <span data-ttu-id="44234-144">Откройте Рендерерманажер. cpp в редакторе кода и замените автоматически созданный код следующим кодом.</span><span class="sxs-lookup"><span data-stu-id="44234-144">Open RendererManager.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerCPP](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanagercpp)]

6. <span data-ttu-id="44234-145">Откройте Трианглерендерер. h в редакторе кода и замените автоматически созданный код следующим кодом.</span><span class="sxs-lookup"><span data-stu-id="44234-145">Open TriangleRenderer.h in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.h#trianglerendererh)]

7. <span data-ttu-id="44234-146">Откройте Трианглерендерер. cpp в редакторе кода и замените автоматически созданный код следующим кодом.</span><span class="sxs-lookup"><span data-stu-id="44234-146">Open TriangleRenderer.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererCPP](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.cpp#trianglerenderercpp)]

8. <span data-ttu-id="44234-147">Откройте файл stdafx. h в редакторе кода и замените автоматически созданный код следующим кодом.</span><span class="sxs-lookup"><span data-stu-id="44234-147">Open stdafx.h in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#StdafxH](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/stdafx.h#stdafxh)]

9. <span data-ttu-id="44234-148">Откройте DllMain. cpp в редакторе кода и замените автоматически созданный код следующим кодом.</span><span class="sxs-lookup"><span data-stu-id="44234-148">Open dllmain.cpp in the Code Editor and replace the automatically generated code with the following code.</span></span>

     [!code-cpp[System.Windows.Interop.D3DImage#DllMain](~/samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/dllmain.cpp#dllmain)]

10. <span data-ttu-id="44234-149">Откройте D3DContent. DEF в редакторе кода.</span><span class="sxs-lookup"><span data-stu-id="44234-149">Open D3DContent.def in the code editor.</span></span>

11. <span data-ttu-id="44234-150">Замените автоматически созданный код следующим кодом.</span><span class="sxs-lookup"><span data-stu-id="44234-150">Replace the automatically generated code with the following code.</span></span>

    ```cpp
    LIBRARY "D3DContent"

    EXPORTS

    SetSize
    SetAlpha
    SetNumDesiredSamples
    SetAdapter

    GetBackBufferNoRef
    Render
    Destroy
    ```

12. <span data-ttu-id="44234-151">Выполните построение проекта.</span><span class="sxs-lookup"><span data-stu-id="44234-151">Build the project.</span></span>

## <a name="next-steps"></a><span data-ttu-id="44234-152">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="44234-152">Next Steps</span></span>

- <span data-ttu-id="44234-153">Размещение содержимого Direct3D9 в приложении WPF.</span><span class="sxs-lookup"><span data-stu-id="44234-153">Host the Direct3D9 content in a WPF application.</span></span> <span data-ttu-id="44234-154">Дополнительные сведения см. в разделе [Пошаговое руководство: Размещение содержимого Direct3D9 в WPF](walkthrough-hosting-direct3d9-content-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="44234-154">For more information, see [Walkthrough: Hosting Direct3D9 Content in WPF](walkthrough-hosting-direct3d9-content-in-wpf.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="44234-155">См. также</span><span class="sxs-lookup"><span data-stu-id="44234-155">See also</span></span>

- <xref:System.Windows.Interop.D3DImage>
- [<span data-ttu-id="44234-156">Вопросы производительности, связанные с взаимодействием Direct3D9 и WPF</span><span class="sxs-lookup"><span data-stu-id="44234-156">Performance Considerations for Direct3D9 and WPF Interoperability</span></span>](performance-considerations-for-direct3d9-and-wpf-interoperability.md)
- [<span data-ttu-id="44234-157">Пошаговое руководство: Размещение содержимого Direct3D9 в WPF</span><span class="sxs-lookup"><span data-stu-id="44234-157">Walkthrough: Hosting Direct3D9 Content in WPF</span></span>](walkthrough-hosting-direct3d9-content-in-wpf.md)
