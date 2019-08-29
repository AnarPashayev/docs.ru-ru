---
title: Взаимодействие на уровне машинного кода — .NET
description: Сведения о взаимодействии с компонентами на базе машинного кода в .NET.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 3ca213bc7228d2e4337607df2d47b334c5bea14f
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106802"
---
# <a name="native-interoperability"></a><span data-ttu-id="22e88-103">Взаимодействие на уровне машинного кода</span><span class="sxs-lookup"><span data-stu-id="22e88-103">Native interoperability</span></span>

<span data-ttu-id="22e88-104">В следующих статьях показаны различные способы взаимодействия на уровне машинного кода в .NET.</span><span class="sxs-lookup"><span data-stu-id="22e88-104">The following articles show the various ways of doing "native interoperability" in .NET.</span></span>

<span data-ttu-id="22e88-105">Для обращения к машинному коду может быть несколько причин:</span><span class="sxs-lookup"><span data-stu-id="22e88-105">There are a few reasons why you'd want to call into native code:</span></span>

- <span data-ttu-id="22e88-106">Операционные системы включают большой объем API-интерфейсов, отсутствующих в управляемых библиотеках классов.</span><span class="sxs-lookup"><span data-stu-id="22e88-106">Operating systems come with a large volume of APIs that aren't present in the managed class libraries.</span></span> <span data-ttu-id="22e88-107">Яркий пример такого сценария — доступ к функциям управления оборудованием или операционной системой.</span><span class="sxs-lookup"><span data-stu-id="22e88-107">A prime example for this scenario would be access to hardware or operating system management functions.</span></span>
- <span data-ttu-id="22e88-108">Взаимодействие с другими компонентами, имеющими или способными создавать ABI в стиле C (ABI машинного кода), например код Java, предоставляемый с помощью [Java Native Interface (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/), или любой другой управляемый язык, способный создавать компоненты машинного кода.</span><span class="sxs-lookup"><span data-stu-id="22e88-108">Communicating with other components that have or can produce C-style ABIs (native ABIs), such as Java code that is exposed via [Java Native Interface (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) or any other managed language that could produce a native component.</span></span>
- <span data-ttu-id="22e88-109">Большая часть устанавливаемого программного обеспечения Windows, например пакет Microsoft Office, регистрирует COM-компоненты, которые представляют свои программы и позволяют разработчикам автоматизировать или использовать их.</span><span class="sxs-lookup"><span data-stu-id="22e88-109">On Windows, most of the software that gets installed, such as the Microsoft Office suite, registers COM components that represent their programs and allow developers to automate them or use them.</span></span> <span data-ttu-id="22e88-110">Для этого также требуется взаимодействие на уровне машинного кода.</span><span class="sxs-lookup"><span data-stu-id="22e88-110">This also requires native interoperability.</span></span>

<span data-ttu-id="22e88-111">Приведенный список охватывает не все возможные ситуации и сценарии, в которых разработчику может потребоваться взаимодействие с компонентами машинного кода.</span><span class="sxs-lookup"><span data-stu-id="22e88-111">The previous list doesn't cover all of the potential situations and scenarios in which the developer would want/like/need to interface with native components.</span></span> <span data-ttu-id="22e88-112">Например, библиотека классов .NET использует поддержку взаимодействия на уровне машинного кода для реализации значительного количества своих API, таких как поддержка и использование консоли, доступ к файловой системе и др.</span><span class="sxs-lookup"><span data-stu-id="22e88-112">.NET class library, for instance, uses the native interoperability support to implement a fair number of its APIs, like console support and manipulation, file system access and others.</span></span> <span data-ttu-id="22e88-113">Однако важно помнить, что при необходимости такая возможность существует.</span><span class="sxs-lookup"><span data-stu-id="22e88-113">However, it's important to note that there's an option if needed.</span></span>

> [!NOTE]
> <span data-ttu-id="22e88-114">Большинство примеров в этом разделе приводятся для всех трех поддерживаемых платформ .NET Core (Windows, Linux и macOS).</span><span class="sxs-lookup"><span data-stu-id="22e88-114">Most of the examples in this section will be presented for all three supported platforms for .NET Core (Windows, Linux and macOS).</span></span> <span data-ttu-id="22e88-115">Но для краткости и наглядности приведен лишь один пример, использующий имена и расширения файлов Windows ("dll" для библиотек).</span><span class="sxs-lookup"><span data-stu-id="22e88-115">However, for some short and illustrative examples, just one sample is shown that uses Windows filenames and extensions (that is, "dll" for libraries).</span></span> <span data-ttu-id="22e88-116">Это сделано исключительно ради удобства и не означает, что на Linux и macOS такие функции недоступны.</span><span class="sxs-lookup"><span data-stu-id="22e88-116">This doesn't mean that those features aren't available on Linux or macOS, it was done merely for convenience sake.</span></span>

## <a name="see-also"></a><span data-ttu-id="22e88-117">См. также</span><span class="sxs-lookup"><span data-stu-id="22e88-117">See also</span></span>

- [<span data-ttu-id="22e88-118">Вызов неуправляемого кода (P/Invoke)</span><span class="sxs-lookup"><span data-stu-id="22e88-118">Platform Invoke (P/Invoke)</span></span>](pinvoke.md)
- [<span data-ttu-id="22e88-119">Маршалинг типов</span><span class="sxs-lookup"><span data-stu-id="22e88-119">Type marshaling</span></span>](type-marshaling.md)
- [<span data-ttu-id="22e88-120">Рекомендации по использованию взаимодействия на уровне машинного кода</span><span class="sxs-lookup"><span data-stu-id="22e88-120">Native interoperability best practices</span></span>](best-practices.md)
