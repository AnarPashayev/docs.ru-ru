---
title: Практическое руководство. Использование программы Svcutil.exe для проверки скомпилированного кода службы
ms.date: 03/30/2017
ms.assetid: d0d820fb-41c2-45b8-8f22-0fa5aeebbbaa
ms.openlocfilehash: 599f5624b7eb0c32cbcc0a78e6c7f989ce470b58
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59312427"
---
# <a name="how-to-use-svcutilexe-to-validate-compiled-service-code"></a>Практическое руководство. Использование программы Svcutil.exe для проверки скомпилированного кода службы
Можно использовать [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) для обнаружения ошибок в реализациях службы и конфигурациях без размещения службы.  
  
### <a name="to-validate-a-service"></a>Проверка службы  
  
1. Скомпилируйте службу в исполняемый файл и одну или более зависимых сборок.  
  
2. Откройте окно командной строки SDK.  
  
3. Из командной строки запустите средство Svcutil.exe, используя следующий формат. Дополнительные сведения о различных параметрах см. в разделе Validationsection службы из [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) раздела.  
  
    ```  
    svcutil.exe /validate /serviceName:<serviceConfigName>  <assemblyPath>*  
    ```  
  
     Чтобы указать имя конфигурации службы для проверки, необходимо использовать параметр `/serviceName`.  
  
     Аргумент `assemblyPath` задает путь к исполняемому файлу для службы и одной или более сборок, которые содержат типы службы для проверки. Исполняемая сборка должна содержать связанный файл конфигурации для предоставления конфигурации службы. Для предоставления нескольких сборок можно использовать стандартные подстановочные знаки командной строки.  
  
## <a name="example"></a>Пример  
 Следующая команда проверяет службу myServiceName, реализованную в исполняемом файле myServiceHost.exe.  Автоматически загружается файл конфигурации для этой службы (myServiceHost.exe.config).  
  
```  
svcutil /validate /serviceName:myServiceName myServiceHost.exe  
```  
  
## <a name="see-also"></a>См. также

- [Служебная программа для метаданных ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
