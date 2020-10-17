---
title: 'NETSDK1005 и NETSDK1047: в файле ресурсов отсутствует целевой объект'
description: Устранение проблемы отсутствия целевого объекта в файле ресурса.
author: sfoslund
ms.topic: error-reference
ms.date: 10/09/2020
f1_keywords:
- NETSDK1005
- NETSDK1047
ms.openlocfilehash: 6c22fd8c79c2ac6e024b46b4f67e08011d42efc6
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2020
ms.locfileid: "91957120"
---
# <a name="netsdk1005-and-netsdk1047-asset-file-is-missing-target"></a><span data-ttu-id="798fb-103">NETSDK1005 и NETSDK1047: в файле ресурсов отсутствует целевой объект</span><span class="sxs-lookup"><span data-stu-id="798fb-103">NETSDK1005 and NETSDK1047: Asset file is missing target</span></span>

<span data-ttu-id="798fb-104">**Эта статья относится к:** ✔️ пакету SDK для .NET 2.1.100 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="798fb-104">**This article applies to:** ✔️ .NET 2.1.100 SDK and later versions</span></span>

<span data-ttu-id="798fb-105">Когда пакет SDK для .NET выдает ошибку NETSDK1005 или NETSDK1047, это означает, что в файле ресурсов проекта отсутствуют сведения об одной из целевых платформ.</span><span class="sxs-lookup"><span data-stu-id="798fb-105">When the .NET SDK issues error NETSDK1005 or NETSDK1047, the project's assets file is missing information on one of your target frameworks.</span></span> <span data-ttu-id="798fb-106">Обычно это можно исправить, убедившись в том, что выполняется восстановление и что отсутствующее целевое значение включено в свойство `TargetFrameworks` проекта.</span><span class="sxs-lookup"><span data-stu-id="798fb-106">This can usually be fixed by ensuring that restore is run and that the missing target value is included in the `TargetFrameworks` property of your project.</span></span>

> [!NOTE]
> <span data-ttu-id="798fb-107">Известна проблема с ранними сборками предварительной версии 8 .NET 5 при использовании с предварительными версиями Visual Studio 16.8, которые привели к этой ошибке.</span><span class="sxs-lookup"><span data-stu-id="798fb-107">There was a known issue with early builds of .NET 5 preview 8 when used with versions of Visual Studio 16.8 previews which resulted in this error.</span></span> <span data-ttu-id="798fb-108">В частности, если отсутствующий целевой объект — это `net5.0-windows7.0` или `net5.0`, убедитесь, что выполнено обновление до последних версий Visual Studio и пакета SDK для .NET 5.</span><span class="sxs-lookup"><span data-stu-id="798fb-108">Specifically, if the missing target is `net5.0-windows7.0` or `net5.0`, ensure that you have updated to the latest versions of Visual Studio and the .NET 5 SDK.</span></span>
