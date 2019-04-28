---
title: Предложение Order By (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryOrderBy
- vb.QueryAscending
- vb.QueryDescending
helpviewer_keywords:
- queries [Visual Basic], Order By
- Order By clause [Visual Basic]
- Order By statement [Visual Basic]
ms.assetid: fa911282-6b81-44c7-acfa-46b5bb93df75
ms.openlocfilehash: 1c84a4cdb4a149154d459ca4d9c290ed360d1772
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "61712569"
---
# <a name="order-by-clause-visual-basic"></a>Предложение Order By (Visual Basic)
Указывает порядок сортировки для результата запроса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a>Части  
 `orderExp1`  
 Обязательный. Одно или несколько полей из текущего результата запроса, определяющие порядок возвращаемых значений. Имена полей должны быть разделены запятыми (,). Можно определить каждое поле как отсортированный в порядке возрастания или убывания, используя `Ascending` или `Descending` ключевые слова. Если не `Ascending` или `Descending` указывается ключевое слово, порядок сортировки по возрастанию. Поля порядка сортировки получают приоритет слева направо.  
  
## <a name="remarks"></a>Примечания  
 Можно использовать `Order By` предложение для сортировки результатов запроса. `Order By` Предложение можно сортировать только результат на основании переменная диапазона для текущей области. Например `Select` предложение вводит новую область в выражении запроса с помощью новых переменных итераций для данной области. Переменные, определенные до диапазона `Select` предложение в запросе не доступны после `Select` предложение. Таким образом Если есть необходимость упорядочить результаты по полю, которое недоступно в `Select` предложение, необходимо поместить `Order By` предложение перед `Select` предложение. Один пример при пришлось бы сделать это — необходимо выполнить сортировку по полям, которые не будут возвращены как часть результата запроса.  
  
 По возрастанию и убыванию для поля определяется с использованием реализации <xref:System.IComparable> интерфейса для типа данных поля. Если тип данных не реализует <xref:System.IComparable> интерфейс, порядок сортировки учитывается.  
  
## <a name="example"></a>Пример  
 В следующем запросе используется выражение `From` предложение для объявления переменной диапазона `book` для `books` коллекции. `Order By` Предложение сортирует результаты запроса по цене по возрастанию (по умолчанию). Книги с такой же цене сортируются по названию в порядке возрастания. `Select` Предложение выбирает `Title` и `Price` свойствами, что значения, возвращаемые запросом.  
  
 [!code-vb[VbSimpleQuerySamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#24)]  
  
## <a name="example"></a>Пример  
 В следующем запросе используется выражение `Order By` предложение для сортировки результатов запроса по цене в порядке убывания. Книги с такой же цене сортируются по названию в порядке возрастания.  
  
 [!code-vb[VbSimpleQuerySamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#25)]  
  
## <a name="example"></a>Пример  
 В следующем запросе используется выражение `Select` предложение, чтобы выбрать название книги, цена, дата публикации и создавать. Затем заполняет `Title`, `Price`, `PublishDate`, и `Author` поля переменной диапазона для новой области. `Order By` Предложение упорядочивает новую переменную диапазона, имя автора, название и цена. Каждый столбец сортируется в порядке по умолчанию (по возрастанию).  
  
 [!code-vb[VbSimpleQuerySamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#26)]  
  
## <a name="see-also"></a>См. также

- [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) (Знакомство с LINQ в Visual Basic)
- [Запросы](../../../visual-basic/language-reference/queries/index.md)
- [Предложение Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Предложение From](../../../visual-basic/language-reference/queries/from-clause.md)
