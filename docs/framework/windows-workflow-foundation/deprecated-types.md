---
title: Устаревшие типы в Windows Workflow Foundation
ms.date: 03/30/2017
ms.assetid: 4aebe928-a964-4c1c-abf7-0dbbd3604b13
ms.openlocfilehash: c8325e60d708b53e1701a980355d5d2bf20e8a4b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64644959"
---
# <a name="deprecated-types-in-windows-workflow-foundation"></a>Устаревшие типы в Windows Workflow Foundation
В .NET 4 команда разработки по рабочим процессам представила полностью новую подсистему рабочих процессов в пространстве имен <xref:System.Activities>. С появлением бета-версии .NET 4.5 Мы отмечаем большинство типов в «WF 3» <xref:System.Workflow.Activities>, <xref:System.Workflow.ComponentModel>, и <xref:System.Workflow.Runtime> пространства имен, как устаревшие.  
  
## <a name="obsolete-namespaces-and-tools"></a>Устаревшие пространства имен и средства  
 Следующие сборки содержат один и более открытых типов, которые станут устаревшими.  
  
- System.Workflow.Activities.dll  
  
- System.Workflow.ComponentModel.dll  
  
- System.Workflow.Runtime.dll  
  
- System.WorkflowServices.dll  
  
- Microsoft.Workflow.DebugController.dll  
  
- Microsoft.Workflow.Compiler.exe  
  
- Wfc.exe  
  
 В результате этого клиенты, использующие устаревшие API WF 3, увидят предупреждения при сборке с сообщением следующего вида:  
  
 **Предупреждение BC40000. X устарело: WF 3 являются устаревшими. Используйте WF 4.** В одном из последующих выпусков (не в 4.5) типы будут удалены из .NET Framework, но временной промежуток до этого еще не определен. Текущий шаг позволяет донести наши планы до клиентов и дает им достаточно времени для перехода на новую модель WF4. Мы Конечно, продолжит поддерживать эти типы WF 3 в разделе [политики жизненного цикла поддержки Microsoft](https://aka.ms/MicrosoftSupportLifecycle). Существующие приложения WF3 будет выполняться без проблем на .NET 4.5 и Visual Studio 2012 будет поддерживать новых и существующих решений на основе WF3.  
  
 Основанные на правилах типы в пространстве имен <xref:System.Workflow.Activities.Rules>, не имеющие замены в WF 4.5, не устарели.  
  
 Клиенты, желающие перевести свои приложения на WF 4 будет найти полезную информацию в [руководство по миграции рабочего процесса 4](migration-guidance.md).
