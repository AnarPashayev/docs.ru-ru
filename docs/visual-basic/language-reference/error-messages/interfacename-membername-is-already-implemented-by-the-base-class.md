---
title: "'<interfacename>. <membername>«уже реализован базовым классом»<baseclassname>\". Повторная реализация <type> предполагается, что"
ms.date: 07/20/2015
f1_keywords:
- vbc42015
- bc42015
helpviewer_keywords:
- BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
ms.openlocfilehash: 5943eff5fa7e68da9905e3e589eea264c06943c1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593321"
---
# <a name="interfacenamemembername-is-already-implemented-by-the-base-class-baseclassname-re-implementation-of-type-assumed"></a>"\<имя_интерфейса >. \<имя_члена > "уже реализован базовым классом\<имя_базового_класса >". Повторная реализация \<тип > предполагается, что
Свойство, процедура или событие в производном классе использует `Implements` предложение, задающее элемент интерфейса, который уже реализован в базовом классе.  
  
 Производный класс может повторно реализовать элемент интерфейса, который реализован его базовым классом. Это не та же переопределяющая реализация базового класса. Для получения дополнительной информации см. [Implements](../../../visual-basic/language-reference/statements/implements-clause.md).  
  
 По умолчанию данное сообщение является предупреждением. Сведения о сокрытии предупреждений или обработке предупреждений как ошибок см. в разделе [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Идентификатор ошибки:** BC42015  
  
## <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Если вы собираетесь реализовать элемент интерфейса, вам не нужно предпринимать никаких действий. Код в производном классе получает доступ к повторно реализованному элементу только при использовании `MyBase` ключевое слово для доступа к реализации базового класса.  
  
- Если вы не собираетесь реализовать элемент интерфейса, удалите предложение `Implements` из свойства, процедуры или объявления события.  
  
## <a name="see-also"></a>См. также

- [Интерфейсы](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
