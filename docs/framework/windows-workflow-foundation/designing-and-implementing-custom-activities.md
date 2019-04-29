---
title: Разработка и реализация настраиваемых действий
ms.date: 03/30/2017
ms.assetid: 4e30e63d-6e33-4842-a7a4-ce807cef1fad
ms.openlocfilehash: 61a5de5a15835c728c18c0136952cf7ffdbaf000
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945851"
---
# <a name="designing-and-implementing-custom-activities"></a>Разработка и реализация настраиваемых действий
Настраиваемые действия в [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] создаются либо посредством сборки системных действий в составные действия, либо путем создания новых типов, производных от <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity> или <xref:System.Activities.NativeActivity>. В этом разделе описываются способы создания пользовательских действий обоими способами.  
  
> [!IMPORTANT]
>  Настраиваемые действия по умолчанию отображаются в конструкторе рабочих процессов в виде простого прямоугольника с именем действия. Для создания настраиваемого визуального представления действия в конструкторе рабочих процессов также необходимо создать пользовательский конструктор. Дополнительные сведения см. в разделе [шаблонов и с помощью конструкторов пользовательских действий](using-custom-activity-designers-and-templates.md).  
  
## <a name="in-this-section"></a>В этом разделе  
 [Параметры разработки действий](activity-authoring-options-in-wf.md)  
 Описывает стили разработки, доступные в [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)].  
  
 [Использование настраиваемого действия](using-a-custom-activity.md)  
 Описывает, как добавить пользовательское действие в проект рабочего процесса.  
  
  [Создание асинхронных действий](creating-asynchronous-activities-in-wf.md)  
 Описывает создание асинхронных действий.  
  
 [Настройка проверки действий](configuring-activity-validation.md)  
 Описывает, как проверка действия может быть использована для выявления ошибок в конфигурации действия до его выполнения.  
  
 [Создание действия в среде выполнения](creating-an-activity-at-runtime-with-dynamicactivity.md)  
 Описывает, как создавать действия во время выполнения с помощью <xref:System.Activities.DynamicActivity>.  
  
 [Свойства выполнения рабочего процесса](workflow-execution-properties.md)  
 Описывает, как использовать свойства выполнения рабочего процесса для добавления определенных свойств контекста к среде действия.  
  
 [Использование делегатов действий](using-activity-delegates.md)  
 Описывает создание и использование действий, содержащих делегаты действий.
  
 [Использование расширений действий](using-activity-extensions.md)  
 Описывает, как создавать и использовать расширения действий.  
  
 [Использование каналов OData из рабочего процесса](consuming-odata-feeds-from-a-workflow.md)  
 Описывает различные методы для вызова службы данных WCF из рабочего процесса.  
  
 [Определение области и видимости действия](activity-definition-scoping-and-visibility.md)  
 Описывает параметры и правила для определения области данных и видимости элементов для действий.
