---
title: Пример таблицы UriTemplate
ms.date: 03/30/2017
ms.assetid: 5dd1d38f-1989-4c64-820d-821f5a02216a
ms.openlocfilehash: caa8e2aab82283b8ca41dd650cd299485d922305
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294941"
---
# <a name="uritemplate-table-sample"></a>Пример таблицы UriTemplate

Класс <xref:System.UriTemplateTable> предоставляет структуру ассоциативной таблицы, подобную словарю, для работы с набором экземпляров `UriTemplate`. Конкретные универсальные коды ресурса (URI) могут эффективно сравниваться со всеми шаблонами в таблице, после чего могут извлекаться данные, связанные с совпадающим шаблоном.  
  
 Данный пример демонстрирует следующие ключевые понятия, связанные с классом `UriTemplateTable`:  
  
- Синтаксис для создания экземпляров `UriTemplateTable`.  
  
- Занесение в `UriTemplateTable` набора пар ключ/значение.  
  
- Сравнение потенциального универсального кода ресурса (URI) по таблице с использованием <xref:System.UriTemplateTable.MatchSingle%2A>.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Настройка, сборка и выполнение образца  
  
1. Чтобы создать выпуск решения на языке C# или Visual Basic .NET, следуйте инструкциям в разделе [Building the Windows Communication Foundation Samples](building-the-samples.md).  
  
2. Чтобы запустить пример в конфигурации с одним или несколькими компьютерами, следуйте инструкциям в разделе [выполнение примеров Windows Communication Foundation](running-the-samples.md).  
  
> [!IMPORTANT]
> Образцы уже могут быть установлены на компьютере. Перед продолжением проверьте следующий каталог (по умолчанию).  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры. Этот образец расположен в следующем каталоге.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateTable`  
  
## <a name="see-also"></a>См. также

- [Диспетчер таблицы UriTemplate](uritemplate-table-dispatcher-sample.md)
- [UriTemplate](uritemplate-sample.md)
