---
title: Проход по тексту при помощи модели автоматизации пользовательского интерфейса
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, traversing text
- text, traversing
- traversing text
ms.assetid: 3ddb3b7b-1d6b-4dba-8678-5a68e868aadb
ms.openlocfilehash: b22da8575fdc4360601946c3cba136466a393895
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/17/2019
ms.locfileid: "71042560"
---
# <a name="traverse-text-using-ui-automation"></a>Проход по тексту при помощи модели автоматизации пользовательского интерфейса
> [!NOTE]
> Эта документация предназначена для разработчиков .NET Framework, желающих использовать управляемые классы [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , заданные в пространстве имен <xref:System.Windows.Automation> . Последние сведения о [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]см. в разделе [API службы автоматизации Windows: Модель автоматизации](https://go.microsoft.com/fwlink/?LinkID=156746)пользовательского интерфейса.  
  
 В этом разделе показано, как использовать [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] для перехода по текстовому содержимому документа шагами приращения <xref:System.Windows.Automation.Text.TextUnit> .  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано, как проходить содержимое поставщика текста автоматизации пользовательского интерфейса. Метод <xref:System.Windows.Automation.Text.TextPatternRange.Move%2A> перемещает конечные точки <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> и <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> диапазона <xref:System.Windows.Automation.Text.TextPatternRange>. Этот диапазон текста обычно является вырожденным диапазоном, представляющим точку вставки текста.  
  
> [!NOTE]
> Поскольку только основанные на тексте внедренные объекты считаются частью текстового потока, такие внедренные объекты, как изображения, не влияют на `Move` или его возвращаемое значение.  
  
[!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
[!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#Navigate](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#navigate)]
[!code-vb[FindText#Navigate](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#navigate)]  
  
 Любой метод, использующий <xref:System.Windows.Automation.Text.TextUnit> , будет откладываться для следующего наибольшего <xref:System.Windows.Automation.Text.TextUnit> , поддерживаемого если указанный <xref:System.Windows.Automation.Text.TextUnit> не поддерживается элементом управления.  
  
## <a name="see-also"></a>См. также

- [Общие сведения об объекте TextPattern модели автоматизации пользовательского интерфейса](ui-automation-textpattern-overview.md)
- [Добавление содержимого в текстовое поле с помощью модели автоматизации пользовательского интерфейса](add-content-to-a-text-box-using-ui-automation.md)
- [Поиск и выделение текста с помощью модели автоматизации пользовательского интерфейса](find-and-highlight-text-using-ui-automation.md)
- [Общие сведения о шаблонах элементов управления модели автоматизации пользовательского интерфейса](ui-automation-control-patterns-overview.md)
- [Шаблоны элементов управления модели автоматизации пользовательского интерфейса для клиентов](ui-automation-control-patterns-for-clients.md)
