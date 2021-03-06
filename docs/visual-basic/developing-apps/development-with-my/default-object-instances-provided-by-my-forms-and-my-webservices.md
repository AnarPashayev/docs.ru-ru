---
title: Экземпляры объектов, которые My.Forms и My.WebServices предоставляют по умолчанию
ms.date: 07/20/2015
helpviewer_keywords:
- My.WebServices object [Visual Basic], developing applications
- My.Forms object [Visual Basic], developing applications
- rapid application development (RAD), My.Forms
- rapid application development (RAD), My.WebServices
ms.assetid: de930027-9108-4f0c-b97c-5e7db4d6ef79
ms.openlocfilehash: 141f2f5f98499498d3c6732f7ae8d0abe6259ed9
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990240"
---
# <a name="default-object-instances-provided-by-myforms-and-mywebservices-visual-basic"></a>Экземпляры объектов, которые My.Forms и My.WebServices предоставляют по умолчанию (Visual Basic)

Объекты [My.Forms](../../language-reference/objects/my-forms-object.md) и [My.WebServices](../../language-reference/objects/my-webservices-object.md) предоставляют доступ к формам, источникам данных и веб-службам XML, используемым вашим приложением. Для этого они используют коллекции *экземпляров по умолчанию* каждого из этих объектов.  
  
## <a name="default-instances"></a>Экземпляры по умолчанию  

 Экземпляр по умолчанию — это экземпляр класса, который предоставляется средой выполнения и не требует объявления и создания экземпляра с помощью инструкций `Dim` и `New`. В следующем примере показано, как раньше можно было объявить и создать экземпляр класса <xref:System.Windows.Forms.Form> с именем `Form1` и как теперь можно получить экземпляр по умолчанию этого класса <xref:System.Windows.Forms.Form> через `My.Forms`.  
  
 [!code-vb[VbVbcnMy#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#5)]  
  
 [!code-vb[VbVbcnMy#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#6)]  
  
 Объект `My.Forms` возвращает коллекцию экземпляров по умолчанию для каждого класса `Form`, существующего в проекте. Аналогичным образом, `My.WebServices` предоставляет экземпляр прокси-класса по умолчанию для каждой веб-службы, на которую вы ссылались в приложении.  
  
## <a name="see-also"></a>См. также

- [Объект My.Forms](../../language-reference/objects/my-forms-object.md)
- [Объект My.WebServices](../../language-reference/objects/my-webservices-object.md)
- [Зависимость My от типа проекта](how-my-depends-on-project-type.md)
