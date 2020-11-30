---
title: Практическое руководство. Запись символов в строку
ms.date: 01/21/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data streams, writing characters to string
- writing characters to strings
- streams, writing characters to strings
- I/O [.NET], writing characters to strings
ms.assetid: 1222cbeb-0760-44bf-9888-914a2a37174b
ms.openlocfilehash: 21661a858cff9fc8bc84d497b4af8bedb1393f0a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734534"
---
# <a name="how-to-write-characters-to-a-string"></a>Практическое руководство. Запись символов в строку

Следующий пример кода демонстрирует синхронную или асинхронную запись символов из массива символов в строку.  
  
## <a name="example-write-characters-synchronously-in-a-console-app"></a>Пример. Синхронная запись символов в консольном приложении  

 В следующем примере используется <xref:System.IO.StringWriter> для синхронной записи пяти символов в объект <xref:System.Text.StringBuilder>.
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example-write-characters-asynchronously-in-a-wpf-app"></a>Пример. Запись символов в асинхронном режиме в приложении WPF

 Ниже приведен пример кода за приложением WPF. При загрузке окна пример асинхронным способом считывает все символы из элемента управления <xref:System.Windows.Controls.TextBox> и сохраняет их в массиве. Затем он асинхронно записывает все буквы и пробелы в элемент управления <xref:System.Windows.Controls.TextBlock>, размещая их на отдельных строках.  
  
 [!code-csharp[StreamReaderWriter](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[StreamReaderWriter](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a>См. также

- <xref:System.IO.StringWriter>  
- <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>  
- <xref:System.Text.StringBuilder>  
- [Файловый и потоковый ввод-вывод](index.md)  
- [Асинхронный файловый ввод-вывод](asynchronous-file-i-o.md)  
- [Практическое руководство. Перечисление каталогов и файлов](how-to-enumerate-directories-and-files.md)  
- [Практическое руководство. Считывание данных из нового файла и запись в этот файл](how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Практическое руководство. Открытие файла журнала и добавление в него данных](how-to-open-and-append-to-a-log-file.md)  
- [Практическое руководство. Чтение текста из файла](how-to-read-text-from-a-file.md)  
- [Практическое руководство. Запись текста в файл](how-to-write-text-to-a-file.md)  
- [Практическое руководство. Считывание символов из строки](how-to-read-characters-from-a-string.md)
