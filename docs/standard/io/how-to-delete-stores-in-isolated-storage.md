---
title: Практическое руководство. Удаление хранилищ из области изолированного хранения
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- stores, deleting
- data stores, deleting
- deleting stores
- removing stores
- isolated storage, deleting stores
- storing data using isolated storage, deleting stores
- data storage using isolated storage, deleting stores
ms.assetid: 3947e333-5af6-4601-b2f1-24d4d6129cf3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a935ec663dd178d35aff745e907d2aae48e5b65c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64622583"
---
# <a name="how-to-delete-stores-in-isolated-storage"></a>Практическое руководство. Удаление хранилищ из области изолированного хранения
Класс <xref:System.IO.IsolatedStorage.IsolatedStorageFile> предоставляет два метода для удаления файлов изолированного хранилища.  
  
- Метод экземпляра <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> не требует аргументов и удаляет хранилище, которое его вызывает. Для данной операции не требуется никаких разрешений. Код, имеющий доступ к хранилищу, может удалить данные внутри него полностью или выборочно.  
  
- Статический метод <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> принимает значение перечисления <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> и удаляет все хранилища пользователя, выполняющего этот код. Для выполнения операции требуется разрешение <xref:System.Security.Permissions.IsolatedStorageFilePermission> для значения <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> .  
  
## <a name="example"></a>Пример  
 В следующем примере кода демонстрируется использование статических методов и методов экземпляра <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> . Класс получает два хранилища: одно — изолированное по пользователю и сборке, другое — изолированное по пользователю, домену и сборке. Затем изолированное по пользователю, домену и сборке хранилище удаляется вызовом метода <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> файла изолированного хранилища  `isoStore1`. Далее вызовом статического метода <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>удаляются все оставшиеся хранилища пользователя.  
  
 [!code-cpp[Conceptual.IsolatedStorage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.IsolatedStorage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source3.cs#3)]
 [!code-vb[Conceptual.IsolatedStorage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source3.vb#3)]  
  
## <a name="see-also"></a>См. также

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Изолированное хранилище](../../../docs/standard/io/isolated-storage.md)
