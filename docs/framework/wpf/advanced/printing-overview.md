---
title: Общие сведения о печати
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print path [WPF], XPS
- printers [WPF], XPSDrv-based
- printing [WPF]
- PrintQueue class PrintServer class [WPF]
- XML Paper Specification (XPS) file format
- XPS (XML Paper Specification) file format
- XPSDrv-based printers
- GDI print path [WPF]
ms.assetid: 0de8ac41-9aa6-413d-a121-7aa6f41539b1
ms.openlocfilehash: b6de7aab77c168f353b39b44853fc224cbf0244d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/04/2019
ms.locfileid: "70254081"
---
# <a name="printing-overview"></a>Общие сведения о печати
С Microsoft .NET Framework разработчики приложений, использующие Windows Presentation Foundation (WPF), имеют богатый новый набор API-интерфейсов для управления печатью и системой печати. В [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] некоторые из усовершенствований управления печатью также доступны для разработчиков, создающих приложения [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], и разработчиков, использующих неуправляемый код. Основой этой новой функциональности является новый формат XPS-файла и путь печати XPS.  
  
 В этом разделе содержатся следующие подразделы.  
  
<a name="introduction_to_XPS"></a>   
## <a name="about-xps"></a>О формате XPS  
 XPS — это формат электронного документа, формат файла очереди и язык описания страницы. Это формат открытого документа, в котором используется [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)], Open Packaging Conventions (OPC) и другие отраслевые стандарты для создания кросс-платформенных документов. XPS упрощает процесс создания, совместного использования, печати, просмотра и архивации цифровых документов. Дополнительные сведения о XPS см. в статье [XPS-документы](/windows/desktop/printdocs/documents).  
  
 Некоторые методы печати содержимого на основе XPS с помощью [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] демонстрируются в [программной печати XPS-файлов](how-to-programmatically-print-xps-files.md). Ссылки на эти примеры могут оказаться полезными при просмотре содержимого этого раздела. (Разработчики неуправляемого кода должны увидеть документацию по [функции MXDC_ESCAPE](/windows/desktop/printdocs/mxdc-escape). Windows Forms разработчики должны использовать API в <xref:System.Drawing.Printing> пространстве имен, который не поддерживает полный путь печати XPS, но поддерживает гибридный путь печати из GDI в XPS. См. раздел **Архитектура способа печати** ниже.)  
  
<a name="XPS_print_path_intro"></a>   
## <a name="xps-print-path"></a>Способ печати XPS  
 Путь печати в формате XPS — это новая функция Windows, которая переопределяет способ обработки печати в приложениях Windows. Так как XPS может заменить язык представления документов (например, RTF), формат диспетчера очереди печати (например, WMF) и язык описания страницы (например, PCL или PostScript); новый способ печати сохраняет формат XPS от публикации приложения до финальной обработки в драйвере или устройстве печати.  
  
 Путь печати XPS основан на модели драйвера принтера XPS (XPSDrv), которая предоставляет несколько преимуществ для разработчиков, таких как [!INCLUDE[TLA#tla_wys](../../../../includes/tlasharptla-wys-md.md)] печать, улучшенная поддержка цветов и значительно улучшенная производительность печати. (Дополнительные сведения о XPSDrv см. в [документации к пакету драйверов Windows](/windows-hardware/drivers/).)  
  
 Работа диспетчера очереди печати для документов XPS в основном такая же, как и в предыдущих версиях Windows. Однако он был усовершенствован для поддержки пути печати XPS в дополнение к существующему пути печати GDI. Новый способ печати изначально использует файл очереди XPS. Хотя драйверы принтера пользовательского режима, написанные для предыдущих версий Windows, продолжат работать, для использования пути печати XPS требуется драйвер принтера XPS (XPSDrv).  
  
 Преимущества пути печати XPS существенны и включают:  
  
- Поддержка печати [!INCLUDE[TLA2#tla_wys](../../../../includes/tla2sharptla-wys-md.md)]  
  
- Встроенная поддержка дополнительных цветовых профилей, включая 32 бита на канал (bpc), CMYK, именованные цвета, n-краски и встроенную поддержку прозрачности и градиентов.  
  
- Улучшенная производительность печати как для .NET Framework [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] , так и для приложений на основе.  
  
- Стандартный промышленный формат XPS.  
  
 Для основных сценариев печати доступен простой и интуитивно понятный API с одной точкой входа для пользовательского интерфейса, конфигурации и отправки задания. Для расширенных сценариев добавлена дополнительная поддержка настройки [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] (или не [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] вообще), синхронной или асинхронной печати и возможностей пакетной печати. Оба параметра обеспечивают поддержку печати в режиме полного или частичного доверия.  
  
 Система XPS была разработана с учетом возможностей расширения. С помощью платформы расширяемости функции и возможности можно добавлять в XPS модульным способом. Функции расширяемости включают следующее.  
  
- Схема печати. Общая схема обновляется регулярно и позволяет быстро расширять возможности устройства. (См. **PrintTicket и PrintCapabilities** ниже.)  
  
- Расширяемый конвейер фильтра. Конвейер фильтра драйвера принтера XPS (XPSDrv) был разработан так, чтобы обеспечить как прямую, так и масштабируемую печать документов XPS. Дополнительные сведения см. в разделе [драйверы принтера XPSDrv](/windows-hardware/drivers/print/xpsdrv-printer-drivers). 
  
### <a name="print-path-architecture"></a>Архитектура способа печати  
 Хотя и приложения, и .NET Framework поддерживают XPS [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] , и Windows Forms приложения используют преобразование GDI в XPS для создания содержимого в формате XPS для драйвера принтера XPS (XPSDrv). [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] Эти приложения не обязаны использовать путь печати XPS и могут продолжать использовать распечатку на основе расширенного метафайла (EMF). Однако большинство функций и улучшений XPS доступны только для приложений, предназначенных для печати XPS.  
  
 Чтобы включить использование принтеров на основе XPSDrv в [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] и Windows Forms приложений, драйвер принтера XPS (XPSDrv) поддерживает преобразование из GDI в формат XPS. Модель XPSDrv также предоставляет конвертер для формата XPS в GDI, [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] чтобы приложения могли печатать документы XPS. Для [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] приложений преобразование XPS в формат GDI выполняется автоматически <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> методами <xref:System.Windows.Xps.XpsDocumentWriter> и <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> класса, когда целевая очередь печати в операции записи не имеет драйвера XPSDrv. (Windows Forms приложения не могут печатать документы XPS.)  
  
 На следующем рисунке показана подсистема печати и определены части, предоставляемые корпорацией Майкрософт, а также части, определяемые поставщиками программного обеспечения и оборудования.  
  
 ![На снимке экрана показана система печати XPS.](./media/printing-overview/xml-paper-specification-print-system.png)  
  
### <a name="basic-xps-printing"></a>Базовая печать XPS  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]определяет как базовый, так и расширенный API. Для приложений, которые не нуждаются в расширенной настройке печати или доступе к полному набору функций XPS, доступна базовая поддержка печати. Базовая поддержка печати предоставляется с помощью элемента управления диалогового окна печати, который требует минимальной конфигурации и представляет знакомый [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. При использовании этой упрощенной модели печати доступны многие функции XPS.  
  
#### <a name="printdialog"></a>PrintDialog  
 Элемент управления предоставляет единую точку входа для [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], настройки и отправки задания XPS. <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> Сведения о том, как создать и использовать элемент управления, см. в разделе [Вызов диалогового окна печати](how-to-invoke-a-print-dialog.md).  
  
### <a name="advanced-xps-printing"></a>Расширенная печать XPS  
 Для доступа к полному набору функций XPS необходимо использовать расширенный API печати. Несколько соответствующих API подробно описаны ниже. Полный список API-интерфейсов пути печати XPS см. в <xref:System.Windows.Xps> разделе <xref:System.Printing> ссылки на пространства имен и.  
  
#### <a name="printticket-and-printcapabilities"></a>PrintTicket и PrintCapabilities  
 Классы <xref:System.Printing.PrintTicket> и<xref:System.Printing.PrintCapabilities> являются основой расширенных функций XPS. Оба типа объектов представляют собой форматированные структуры [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] возможностей печати, таких как сортировка, двусторонняя печать, сшивание и т. д. Эти структуры определяются схемой печати. Объект <xref:System.Printing.PrintTicket> указывает принтеру, как обрабатывать задание печати. Класс <xref:System.Printing.PrintCapabilities> определяет возможности принтера. Запрашивая возможности принтера, можно создать <xref:System.Printing.PrintTicket>, который использует все преимущества поддерживаемых возможностей принтера. Аналогичным образом можно избежать неподдерживаемых функций.  
  
 В следующем примере демонстрируется, как запрашивать <xref:System.Printing.PrintCapabilities> принтера и создавать <xref:System.Printing.PrintTicket> с помощью кода.  
  
 [!code-cpp[xpscreate#PrinterCapabilities](~/samples/snippets/cpp/VS_Snippets_Wpf/XpsCreate/CPP/XpsCreate.cpp#printercapabilities)]
 [!code-csharp[xpscreate#PrinterCapabilities](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsCreate/CSharp/XpsCreate.cs#printercapabilities)]
 [!code-vb[xpscreate#PrinterCapabilities](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsCreate/visualbasic/xpscreate.vb#printercapabilities)]  
  
#### <a name="printserver-and-printqueue"></a>PrintServer и PrintQueue  
 Класс <xref:System.Printing.PrintServer> представляет сетевой сервер печати, а класс <xref:System.Printing.PrintQueue> представляет принтер и связанную с ним очередь выходных заданий. Вместе эти интерфейсы API позволяют выполнять расширенное управление заданиями печати сервера. Объект <xref:System.Printing.PrintServer> или один из его производных классов используется для управления <xref:System.Printing.PrintQueue>. Метод <xref:System.Printing.PrintQueue.AddJob%2A> используется для вставки нового задания печати в очередь.  
  
 В следующем примере демонстрируется создание <xref:System.Printing.LocalPrintServer> и доступ к его <xref:System.Printing.PrintQueue> по умолчанию с помощью кода.  
  
 [!code-csharp[xpsprint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[xpsprint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
#### <a name="xpsdocumentwriter"></a>XpsDocumentWriter  
 Объект <xref:System.Windows.Xps.XpsDocumentWriter>с <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> <xref:System.Printing.PrintQueue>множеством методов и используется для записи XPS-документов в. <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> Например, <xref:System.Windows.Xps.XpsDocumentWriter.Write%28System.Windows.Documents.FixedPage%2CSystem.Printing.PrintTicket%29> метод используется для вывода документа XPS и <xref:System.Printing.PrintTicket> синхронно. Метод используется для вывода документа XPS и <xref:System.Printing.PrintTicket> асинхронно. <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%28System.Windows.Documents.FixedDocument%2CSystem.Printing.PrintTicket%29>  
  
 В следующем примере показывается, как создать <xref:System.Windows.Xps.XpsDocumentWriter> с помощью кода.  
  
 [!code-csharp[XpsPrint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[XpsPrint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
 Методы <xref:System.Printing.PrintQueue.AddJob%2A> также предоставляют способы печати. Дополнительные сведения см. в разделе [Печать XPS-файлов программным способом](how-to-programmatically-print-xps-files.md). .  
  
<a name="GDI_Print_Path_intro"></a>   
## <a name="gdi-print-path"></a>Способ печати GDI  
 Хотя [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] приложения изначально поддерживают путь печати XPS, [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] а Windows Forms приложения также могут воспользоваться преимуществами некоторых функций XPS. Драйвер принтера XPS (XPSDrv) может преобразовывать выходные данные на основе GDI в формат XPS. Для расширенных сценариев поддерживается настраиваемое преобразование содержимого с помощью [конвертера документов XPS (Майкрософт) (мксдк)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-). Аналогичным образом <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> <xref:System.Windows.Xps.XpsDocumentWriter> приложения также могут выводить данные в путь печати GDI путем вызова одного из методов или класса и назначения принтера без XPSDrv в качестве целевой очереди печати. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]  

Для приложений, не требующих функциональности или поддержки XPS, текущий путь печати GDI остается неизменным.  
  
- Дополнительные справочные материалы по способу печати GDI и различным параметрам преобразования XPS см. в [статье конвертеры документов XPS (мксдк)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-) и [драйверы принтера XPSDrv](/windows-hardware/drivers/print/xpsdrv-printer-drivers).  
  
<a name="XPS_Driver_Model_intro"></a>   
## <a name="xpsdrv-driver-model"></a>Модель драйвера XPSDrv  
 Путь печати XPS повышает эффективность очереди печати за счет использования XPS в качестве собственного формата очереди печати при печати на принтере или драйвере, поддерживающем XPS. Упрощенный процесс буферизации устраняет необходимость создания промежуточного файла буферизации, например файла данных EMF, перед помещением в очередь документа. Благодаря уменьшению размеров файлов очереди печать XPS может уменьшить сетевой трафик и повысить производительность печати.  
  
 EMF — это закрытый формат, представляющий выходные данные приложения в виде последовательности вызовов GDI для служб отрисовки. В отличие от EMF, формат буферизации XPS представляет фактический документ без необходимости дальнейшей интерпретации при выходе в драйвер принтера на основе XPS (XPSDrv). Драйверы могут работать непосредственно с данными в этом формате. Эта возможность устраняет необходимость преобразования данных и цветового пространства при использовании файлов EMF и драйверов печати на основе GDI.  
  
 Размеры файлов в очереди обычно уменьшаются при использовании документов XPS, предназначенных для драйвера принтера XPS (XPSDrv), по сравнению с их эквивалентами EMF; Однако существуют исключения.  
  
- Очень сложная, многоуровневая или неэффективно созданная векторная графика может быть больше, чем растровая версия того же графического объекта.  
  
- Для отображения экрана XPS-файлы внедряют шрифты устройства, а также шрифты на компьютере; тогда как файлы очереди GDI не внедряют шрифты устройства. Но оба типа шрифтов имеют поднаборы (см. ниже), и драйверы принтера могут удалить шрифты устройства до передачи файла на принтер.  
  
 Уменьшение размера очереди выполняется посредством нескольких механизмов.  
  
- **Поднабор шрифта**. В XPS-файл будут храниться только символы, используемые в фактическом документе.  
  
- **Поддержка расширенной графики**. Встроенная поддержка прозрачности и примитивов градиента позволяет избежать растрирования содержимого в документе XPS.  
  
- **Идентификация общих ресурсов**. Ресурсы, которые используются несколько раз (например, изображение, представляющее эмблему организации), рассматриваются как общие ресурсы и загружаются только один раз.  
  
- **Сжатие ZIP**. Все документы XPS используют сжатие ZIP.  
  
## <a name="see-also"></a>См. также

- <xref:System.Windows.Controls.PrintDialog>
- <xref:System.Windows.Xps.XpsDocumentWriter>
- <xref:System.Windows.Xps.Packaging.XpsDocument>
- <xref:System.Printing.PrintTicket>
- <xref:System.Printing.PrintCapabilities>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.PrintQueue>
- [Разделы практического руководства](printing-how-to-topics.md)
- [Документы в WPF](documents-in-wpf.md)
- [Документы XPS](/windows/desktop/printdocs/documents)
- [Сериализация и хранение документов](document-serialization-and-storage.md)
- [Конвертер документов XPS (Майкрософт) (МКСДК)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-)
