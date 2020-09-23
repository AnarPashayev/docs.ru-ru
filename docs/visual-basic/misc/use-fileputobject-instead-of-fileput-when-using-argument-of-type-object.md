---
title: При использовании аргумента с типом Object применяйте FilePutObject вместо FilePut
ms.date: 07/20/2015
f1_keywords:
- vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
ms.openlocfilehash: c6ae755ad3eca4b1c50b83049885b6cf66f13c07
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/23/2020
ms.locfileid: "91100338"
---
# <a name="use-fileputobject-instead-of-fileput-when-using-argument-of-type-object"></a>При использовании аргумента с типом Object применяйте FilePutObject вместо FilePut

Метод `FilePut` включает аргумент типа `Object`. Чтобы избежать неоднозначности, следует использовать`FilePutObject` вместо `FilePut` .  
  
## <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Замените `FilePut` на `FilePutObject`.  
  
- Приведите аргумент `Object` к более конкретному типу.  
  
- Используйте функциональность объекта `My.Computer.FileSystem` .  
  
## <a name="see-also"></a>См. также

- [My. Computer. FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)
- [My. Computer. FileSystem. WriteAllBytes](xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.WriteAllBytes%2A)
