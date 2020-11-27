---
title: Извлечение метаданных
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WCF], retrieving
ms.assetid: 18d8ba4c-af0f-4827-a50b-4202d767bacc
ms.openlocfilehash: 212ea49418d5e33d79a1b6cf881e2828388c657e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96295513"
---
# <a name="retrieving-metadata"></a>Извлечение метаданных

Извлечение метаданных - это процесс запроса и извлечения метаданных из конечной точки метаданных, например конечной точки метаданных WS-MetadataExchange (MEX) или конечной точки метаданных HTTP/GET.  
  
## <a name="retrieving-metadata-from-the-command-line-using-svcutilexe"></a>Извлечение метаданных с помощью программы командной строки Svcutil.exe  

 Метаданные службы можно получить с помощью WS-MetadataExchange или HTTP/GET, используя средство [служебной программы для метаданных ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) и передав `/target:metadata` параметр и адрес. Средство Svcutil.exe загружает метаданные, расположенные по указанному адресу, и сохраняет файл на диске. Средство Svcutil.exe использует внутри себя экземпляр <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> и загружает из конфигурации конфигурацию конечной точки <xref:System.ServiceModel.Description.IMetadataExchange>, имя которой соответствует схеме адреса, переданного в качестве входных данных средству Svcutil.exe.  
  
## <a name="retrieving-metadata-programmatically-using-the-metadataexchangeclient"></a>Извлечение метаданных программным образом с помощью класса MetadataExchangeClient  

 Windows Communication Foundation (WCF) может получать метаданные службы с помощью стандартизированных протоколов, таких как WS-MetadataExchange и запросов HTTP/GET. Оба эти протокола поддерживаются типом <xref:System.ServiceModel.Description.MetadataExchangeClient>. Чтобы получить метаданные службы с помощью типа <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType>, необходимо указать адрес конечной точки метаданных и необязательную привязку. В роли привязки, используемой экземпляром <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType>, может выступать одна из привязок по умолчанию статического класса <xref:System.ServiceModel.Description.MetadataExchangeBindings>, предоставляемая пользователем привязка или привязка, загруженная из конфигурации конечной точки для контракта `IMetadataExchange`. Кроме того, тип <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> может выполнять разрешение URL-адресов ссылок HTTP на метаданные с помощью типа <xref:System.Net.HttpWebRequest>.  
  
 По умолчанию экземпляр <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> связан с одним экземпляром <xref:System.ServiceModel.ChannelFactory>. Можно изменить или заменить экземпляр <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>, используемый экземпляром <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType>, переопределив виртуальный метод <xref:System.ServiceModel.Description.MetadataExchangeClient.GetChannelFactory%2A>. Аналогично можно изменить или заменить экземпляр <xref:System.Net.HttpWebRequest>, используемый экземпляром <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> для создания запросов HTTP/GET, переопределив виртуальный метод <xref:System.ServiceModel.Description.MetadataExchangeClient.GetWebRequest%2A?displayProperty=nameWithType>.  
  
## <a name="in-this-section"></a>в этом разделе  

 [Практическое руководство. Использование Svcutil.exe для загрузки документов метаданных](how-to-use-svcutil-exe-to-download-metadata-documents.md)  
 Загрузка документов метаданных с помощью средства Svcutil.exe.  
  
 [Практическое руководство. Использование MetadataResolver для динамического получения метаданных привязки](how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md)  
 Получение метаданных привязки динамически во время выполнения с помощью класса <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType>.  
  
 [Практическое руководство. Использование MetadataExchangeClient для получения метаданных](how-to-use-metadataexchangeclient-to-retrieve-metadata.md)  
 Использование класса <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> для загрузки файлов метаданных в объект <xref:System.ServiceModel.Description.MetadataSet?displayProperty=nameWithType>, содержащий объекты <xref:System.ServiceModel.Description.MetadataSection?displayProperty=nameWithType>, для записи в файлы или для других целей.  
  
## <a name="see-also"></a>См. также

- <xref:System.ServiceModel.Description.MetadataExchangeClient>
