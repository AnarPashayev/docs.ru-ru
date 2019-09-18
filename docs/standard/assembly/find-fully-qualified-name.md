---
title: Практическое руководство. Поиск полного имени сборки
ms.date: 08/20/2019
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 009dae23-e1f6-4a64-9a9a-32e4c34802b0
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 4fc670adc80a6f4ce7b36074185dcd3bb85fbc67
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991313"
---
# <a name="how-to-find-an-assemblys-fully-qualified-name"></a><span data-ttu-id="434cc-102">Практическое руководство. Поиск полного имени сборки</span><span class="sxs-lookup"><span data-stu-id="434cc-102">How to: Find an assembly's fully qualified name</span></span>

<span data-ttu-id="434cc-103">Чтобы получить полное имя сборки .NET Framework в глобальном кэше сборок, используйте средство глобального кэша сборок ([Gacutil.exe](../../framework/tools/gacutil-exe-gac-tool.md)).</span><span class="sxs-lookup"><span data-stu-id="434cc-103">To discover the fully qualified name of a .NET Framework assembly in the global assembly cache, use the Global Assembly Cache tool ([Gacutil.exe](../../framework/tools/gacutil-exe-gac-tool.md)).</span></span> <span data-ttu-id="434cc-104">См. практическое руководство по [ Просмотр содержимого глобального кэша сборок](../../framework/app-domains/how-to-view-the-contents-of-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="434cc-104">See [How to: View the contents of the global assembly cache](../../framework/app-domains/how-to-view-the-contents-of-the-gac.md).</span></span>

<span data-ttu-id="434cc-105">Получить полное имя сборки .NET Core или .NET Framework, которая отсутствует в глобальном кэше сборок, можно несколькими способами:</span><span class="sxs-lookup"><span data-stu-id="434cc-105">For .NET Core assemblies, and for .NET Framework assemblies that aren't in the global assembly cache, you can get the fully qualified assembly name in a number of ways:</span></span>

- <span data-ttu-id="434cc-106">Вы можете использовать код для вывода данных в консоль или в переменную либо применить [дизассемблер IL Ildasm.exe](../../framework/tools/ildasm-exe-il-disassembler.md) для просмотра метаданных сборки, которые содержат полное имя.</span><span class="sxs-lookup"><span data-stu-id="434cc-106">You can use code to output the information to the console or to a variable, or you can use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's metadata, which contains the fully qualified name.</span></span>

- <span data-ttu-id="434cc-107">Если сборка уже загружена приложением, то для получения полного имени можно извлечь значение свойства <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="434cc-107">If the assembly is already loaded by the application, you can retrieve the value of the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property to get the fully qualified name.</span></span> <span data-ttu-id="434cc-108">Для получения ссылки на объект <xref:System.Reflection.Assembly> можно использовать свойство <xref:System.Type.Assembly> объекта <xref:System.Type>, определенного в этой сборке.</span><span class="sxs-lookup"><span data-stu-id="434cc-108">You can use the <xref:System.Type.Assembly> property of a <xref:System.Type> defined in that assembly to retrieve a reference to the <xref:System.Reflection.Assembly> object.</span></span> <span data-ttu-id="434cc-109">Иллюстрация приведена в примере.</span><span class="sxs-lookup"><span data-stu-id="434cc-109">The example provides an illustration.</span></span>

- <span data-ttu-id="434cc-110">Если вы знаете путь к файлу сборки в системе, то можете вызвать метод <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> `static` (C#) или `Shared` (Visual Basic), чтобы получить полное имя сборки.</span><span class="sxs-lookup"><span data-stu-id="434cc-110">If you know the assembly's file system path, you can call the `static` (C#) or `Shared` (Visual Basic) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> method to get the fully qualified assembly name.</span></span> <span data-ttu-id="434cc-111">Ниже приведен простой пример.</span><span class="sxs-lookup"><span data-stu-id="434cc-111">The following is a simple example.</span></span>

  ```csharp
  using System;
  using System.Reflection;

  public class Example
  {
     public static void Main()
     {
        Console.WriteLine(AssemblyName.GetAssemblyName(@".\UtilityLibrary.dll"));
     }
  }
  // The example displays output like the following:
  //   UtilityLibrary, Version=1.1.0.0, Culture=neutral, PublicKeyToken=null
  ```

  ```vb
  Imports System.Reflection

  Public Module Example
     Public Sub Main
        Console.WriteLine(AssemblyName.GetAssemblyName(".\UtilityLibrary.dll"))
     End Sub
  End Module
  ' The example displays output like the following:
  '   UtilityLibrary, Version=1.1.0.0, Culture=neutral, PublicKeyToken=null
  ```

- <span data-ttu-id="434cc-112">Вы можете воспользоваться [дизассемблером IL (Ildasm.exe)](../../framework/tools/ildasm-exe-il-disassembler.md), чтобы просмотреть метаданные сборки, которые содержат ее полное имя.</span><span class="sxs-lookup"><span data-stu-id="434cc-112">You can use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's metadata, which contains the fully qualified name.</span></span>

<span data-ttu-id="434cc-113">Подробнее о задании атрибутов сборки, таких как версия, язык и региональные параметры и имя сборки, см. в разделе [Настройка атрибутов сборки](set-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="434cc-113">For more information about setting assembly attributes such as version, culture, and assembly name, see [Set assembly attributes](set-attributes.md).</span></span> <span data-ttu-id="434cc-114">Подробнее о присвоении сборке строгого имени см. в разделе [Создание и использование сборок со строгими именами](create-use-strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="434cc-114">For more information about giving an assembly a strong name, see [Create and use strong-named assemblies](create-use-strong-named.md).</span></span>

## <a name="example"></a><span data-ttu-id="434cc-115">Пример</span><span class="sxs-lookup"><span data-stu-id="434cc-115">Example</span></span>

<span data-ttu-id="434cc-116">В примере ниже показано, как просмотреть полное имя сборки, содержащей указанный класс, в консоли.</span><span class="sxs-lookup"><span data-stu-id="434cc-116">The following example shows how to display the fully qualified name of an assembly containing a specified class to the console.</span></span> <span data-ttu-id="434cc-117">Для получения ссылки на сборку из типа, определенного в этой сборке, используется свойство <xref:System.Type.Assembly?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="434cc-117">It uses the <xref:System.Type.Assembly?displayProperty=nameWithType> property to retrieve a reference to an assembly from a type that's defined in that assembly.</span></span>

```cpp
#using <System.dll>
#using <System.Data.dll>

using namespace System;
using namespace System::Reflection;

ref class asmname
{
public:
    static void Main()
    {
        Type^ t = System::Data::DataSet::typeid;
        String^ s = t->Assembly->FullName->ToString();
        Console::WriteLine("The fully qualified assembly name " +
            "containing the specified class is {0}.", s);
    }
};

int main()
{
    asmname::Main();
}
```

```csharp
using System;
using System.Reflection;

class asmname
{
    public static void Main()
    {
        Type t = typeof(System.Data.DataSet);
        string s = t.Assembly.FullName.ToString();
        Console.WriteLine("The fully qualified assembly name " +
            "containing the specified class is {0}.", s);
    }
}
```

```vb
Imports System
Imports System.Reflection

Class asmname
    Public Shared Sub Main()
        Dim t As Type = GetType(System.Data.DataSet)
        Dim s As String = t.Assembly.FullName.ToString()
        Console.WriteLine("The fully qualified assembly name " +
            "containing the specified class is {0}.", s)
    End Sub
End Class
```

## <a name="see-also"></a><span data-ttu-id="434cc-118">См. также</span><span class="sxs-lookup"><span data-stu-id="434cc-118">See also</span></span>

- [<span data-ttu-id="434cc-119">Имена сборок</span><span class="sxs-lookup"><span data-stu-id="434cc-119">Assembly names</span></span>](names.md)
- [<span data-ttu-id="434cc-120">Создание сборок</span><span class="sxs-lookup"><span data-stu-id="434cc-120">Create assemblies</span></span>](create.md)
- [<span data-ttu-id="434cc-121">Создание и использование сборок со строгими именами</span><span class="sxs-lookup"><span data-stu-id="434cc-121">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
- [<span data-ttu-id="434cc-122">Глобальный кэш сборок</span><span class="sxs-lookup"><span data-stu-id="434cc-122">Global assembly cache</span></span>](../../framework/app-domains/gac.md)
- [<span data-ttu-id="434cc-123">Обнаружение сборок в среде выполнения</span><span class="sxs-lookup"><span data-stu-id="434cc-123">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="434cc-124">Программирование с использованием сборок</span><span class="sxs-lookup"><span data-stu-id="434cc-124">Program with assemblies</span></span>](program.md)
