---
title: Возможности шрифта OpenType
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [WPF], OpenType
- typography [WPF], OpenType font technology
- OpenType font technology [WPF]
ms.assetid: 4061a9d1-fe8b-4921-9e17-18ec7d2e3ea2
ms.openlocfilehash: 3f1f0698afce6e64711e37ac60d0662d65bbee6b
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/25/2019
ms.locfileid: "70016140"
---
# <a name="opentype-font-features"></a>Возможности шрифта OpenType

В этом разделе приводятся общие сведения о некоторых ключевых функциях технологии шрифтов OpenType [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]в.  
  
<a name="overview"></a>   
## <a name="opentype-font-format"></a>Формат шрифта OpenType  
 Формат шрифта OpenType — это расширение [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] формата шрифта, которое добавляет поддержку для данных шрифтов PostScript. Формат шрифтов OpenType был разработан совместно корпорацией Майкрософт и Adobe Corporation. Шрифты OpenType и службы операционной системы, поддерживающие шрифты OpenType, предоставляют пользователям простой способ установки и использования шрифтов независимо от того, содержат [!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)] ли шрифты контуры или CFF (PostScript).  
  
 Формат шрифта OpenType решает следующие задачи разработчика:  
  
- Расширенная поддержка многоплатформенности.  
  
- Улучшенная поддержка международных кодировок.  
  
- Улучшенная защита данных шрифта.  
  
- Меньшие размеры файлов, что повышает эффективность распространения шрифта.  
  
- Расширенная поддержка дополнительного типографского контроля.  
  
> [!NOTE]
> Windows SDK содержит набор образцов шрифтов OpenType, которые можно использовать с [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] приложениями. Эти шрифты обеспечивают большинство функций, приведенных в остальной части этого раздела. Дополнительные сведения см. в разделе [Пакет образцов шрифтов OpenType](sample-opentype-font-pack.md).  
  
 Подробные сведения о формате шрифтов OpenType см. в [спецификации OpenType](https://go.microsoft.com/fwlink/?LinkId=96731) .  
  
### <a name="advanced-typographic-extensions"></a>Дополнительные типографские расширения  
 Расширенные типографские таблицы (Макетные таблицы OpenType) расширяют функциональные возможности шрифтов с [!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)] помощью или CFF контуров. Шрифты макета OpenType содержат дополнительную информацию, расширяющую возможности шрифтов для поддержки международного типографского оформления. Большинство шрифтов OpenType предоставляют только часть общего числа доступных функций OpenType. Шрифты OpenType предоставляют следующие возможности.  
  
- Широкое сопоставление между символами и глифами с поддержкой лигатур, позиционных форм, вариантов и других подстановок шрифтов.  
  
- Поддержка двумерного позиционирования и вложения глифов.  
  
- Явные сведения сценариев и языка, содержащиеся в шрифте, чтобы приложение обработки текста могло соответствующим образом настроить его поведение.  
  
 Макетные таблицы OpenType подробно описаны в разделе [«таблицы файлов шрифтов»](https://www.microsoft.com/typography/otspec/otff.htm) спецификации OpenType.  
  
 В оставшейся части этого обзора представлены широкие возможности и гибкость некоторых визуально интересных функций OpenType, предоставляемых свойствами <xref:System.Windows.Documents.Typography> объекта. Дополнительные сведения об этом объекте см. в разделе [Класс Typography](#typography_class).  
  
<a name="variants"></a>   
## <a name="variants"></a>Варианты  
 Варианты используются для отображения различных типографских стилей, например надстрочных и подстрочных знаков.  
  
### <a name="superscripts-and-subscripts"></a>надстрочные и подстрочные  
 <xref:System.Windows.Documents.Typography.Variants%2A> Свойство позволяет задать надстрочные и подстрочные значения для шрифта OpenType.  
  
 Следующий текст демонстрирует надстрочные знаки для шрифта Palatino Linotype.  
  
 ![Текст, использующий надстрочные знаки OpenType](./media/opentype-font-features/opentype-superscripts.gif "Текст, использующий надстрочные знаки OpenType")  
  
 В следующем примере разметки показано, как определить надстрочные знаки для шрифта Palatino Linotype с помощью свойств <xref:System.Windows.Documents.Typography> объекта.  
  
 [!code-xaml[OpenTypeFontSamples#12](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#12)]  
  
 Следующий текст демонстрирует подстрочные знаки для шрифта Palatino Linotype.  
  
 ![Текст, использующий индексы OpenType](./media/opentype-font-features/opentype-subscripts.gif "Текст, использующий индексы OpenType")  
  
 В следующем примере разметки показано, как определить индексы для шрифта Palatino Linotype с помощью свойств <xref:System.Windows.Documents.Typography> объекта.  
  
 [!code-xaml[OpenTypeFontSamples#13](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#13)]  
  
### <a name="decorative-uses-of-superscripts-and-subscripts"></a>Применение надстрочных и подстрочных знаков в декоративных целях  
 Надстрочные и подстрочные знаки можно также использовать для создания декоративных эффектов текста в смешанном регистре. Следующий текст демонстрирует надстрочный и подстрочный текст для шрифта Palatino Linotype. Обратите внимание, что заглавные буквы не затрагиваются.  
  
 ![Текст, использующий верхние и] нижние индексы OpenType (./media/opentype-font-features/opentype-superscripts-subscripts.gif "Текст, использующий верхние и") нижние индексы OpenType  

 В следующем примере разметки показано, как определить надстрочные и подстрочные индексы для шрифта с помощью свойств <xref:System.Windows.Documents.Typography> объекта.  
  
 [!code-xaml[OpenTypeFontSamples#14](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#14)]  
  
<a name="capitals"></a>   
## <a name="capitals"></a>Capitals  
 Capitals — это набор типографских форм, которые отображают текст в прописных глифах. Когда текст отображается всеми прописными буквами, обычно расстояние между буквами кажется слишком маленьким, а плотность и пропорции символов слишком большими. OpenType поддерживает несколько форматов стилей для прописных букв, включая малые прописные буквы, капительные прописные буквы, заголовочные и прописные. Эти форматы стиля позволяют управлять внешним видом прописных букв.  
  
 Следующий текст демонстрирует стандартные прописные буквы, буквы в стиле SmallCaps и в стиле AllSmallCaps для шрифта Pescadero. В данном случае для всех трех слов используется один и тот же размер шрифта.  
  
 ![Текст, использующий прописные буквы OpenType](./media/opentype-font-features/opentype-capitals.gif "Текст, использующий прописные буквы OpenType")  
  
 В следующем примере разметки показано, как определить прописные буквы для шрифта Pescadero с помощью свойств <xref:System.Windows.Documents.Typography> объекта. При использовании формата SmallCaps начальные прописные буквы игнорируются.  
  
 [!code-xaml[OpenTypeFontSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
### <a name="titling-capitals"></a>Титульные прописные буквы  
 Титульные прописные буквы имеют меньшую плотность и пропорции и разработаны для придания более изысканного вида, чем при использовании обычных прописных букв. Титульные прописные буквы обычно используются в больших размерах шрифтов для заголовков. Следующий текст демонстрирует обычные и титульные прописные буквы для шрифта Pescadero. Обратите внимание на более узкие ножки в тексте во второй строке.  
  
 ![Текст, использующий Титульные прописные буквы OpenType](./media/opentype-font-features/opentype-titling-capitals.gif "Текст, использующий Титульные прописные буквы OpenType")  
  
 В следующем примере разметки показано, как определить Титульные прописные буквы для шрифта Pescadero с помощью свойств <xref:System.Windows.Documents.Typography> объекта.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet17](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet17)]  
  
### <a name="capital-spacing"></a>Интервалы прописных букв  
 Прописной интервал — это функция, которая позволяет обеспечить дополнительные интервалы при использовании в тексте только прописных букв. Прописные буквы обычно разрабатываются для использования вместе со строчными. Интервал между прописной и строчной буквами, который кажется вполне подходящим, может выглядеть слишком маленьким при использовании только прописных букв. Следующий текст демонстрирует обычный и прописной интервалы для шрифта Pescadero.  
  
 ![Текст, использующий прописные расстояния OpenType](./media/opentype-font-features/opentype-capital-spacing.gif "Текст, использующий прописные расстояния OpenType")  
 
 В следующем примере разметки показано, как задать прописные расстояния для шрифта Pescadero с помощью свойств <xref:System.Windows.Documents.Typography> объекта.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet18](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet18)]  
  
<a name="ligatures"></a>   
## <a name="ligatures"></a>Лигатуры  
 Лигатуры — это два (или более) глифа, превращающиеся в один глиф для создания более читаемого или привлекательного текста. Шрифты OpenType поддерживают четыре типа лигатур:  
  
- **Стандартные лигатуры**. Разработаны для улучшения удобочитаемости. Стандартные лигатуры включают fi, fl и ff.  
  
- **Контекстные лигатуры**. Разработаны для улучшения удобочитаемости путем обеспечения более эффективного поведения соединения символов, составляющих лигатуры.  
  
- **Дискретные лигатуры**. Предназначены для украшения и не разрабатывались для удобочитаемости.  
  
- **Исторические лигатуры**. Предназначены для исторических целей и не разрабатывались для удобочитаемости.  
  
 Следующий текст демонстрирует глифы стандартных лигатур для шрифта Pericles.  
  
 ![Текст, использующий стандартные лигатуры OpenType](./media/opentype-font-features/opentype-standard-ligatures.gif "Текст, использующий стандартные лигатуры OpenType")  
  
 В следующем примере разметки показано, как определить стандартные глифы лигатуры для шрифта Pericles с помощью свойств <xref:System.Windows.Documents.Typography> объекта.  
  
 [!code-xaml[OpenTypeFontSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#4)]  
  
 Следующий текст демонстрирует глифы дискретных лигатур для шрифта Pericles.  
  
 ![Текст, использующий дискреционные лигатуры OpenType](./media/opentype-font-features/opentype-discretionary-ligatures.gif "Текст, использующий дискреционные лигатуры OpenType")  
  
 В следующем примере разметки показано, как определить дискреционные глифы лигатуры для шрифта Pericles с помощью свойств <xref:System.Windows.Documents.Typography> объекта.  
  
 [!code-xaml[OpenTypeFontSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#5)]  
  
 По умолчанию шрифты OpenType в [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] используются для включения стандартных лигатур. Например, при использовании шрифта Palatino Linotype стандартные лигатуры fi, ff и fl отображаются как глиф объединенных символов. Обратите внимание, что пары знаков для каждой стандартной лигатуры касаются друг друга.  
  
 ![Текст, использующий стандартные лигатуры OpenType с Palatino Linotype](./media/opentype-font-features/opentype-standard-ligatures-palatino.gif "Текст, использующий стандартные лигатуры OpenType с Palatino Linotype")    
   
 Однако функции стандартных лигатур можно отключить, чтобы стандартные лигатуры, такие как ff, отображались как два отдельных глифа, а не как глиф объединенных символов.  
  
 ![Текст, использующий отключенные стандартные лигатуры OpenType](./media/opentype-font-features/disabled-opentype-standard-ligatures.gif "Текст, использующий отключенные стандартные лигатуры OpenType")  
    
 В следующем примере разметки показано, как отключить стандартные глифы лигатуры для шрифта Palatino Linotype с помощью свойств <xref:System.Windows.Documents.Typography> объекта.  
  
 [!code-xaml[OpenTypeFontSamples#6](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#6)]  
  
<a name="swashes"></a>   
## <a name="swashes"></a>Орнаменты  
 Swash-глифы являются декоративными глифами, которые используют сложную орнаментацию, часто связанную с каллиграфией. Следующий текст отображает стандартные и swash-глифы для шрифта Pescadero.  
  
 ![Текст, использующий стандартные и swash глифы OpenType](./media/opentype-font-features/opentype-standard-swash-glyphs.gif "Текст, использующий стандартные и swash глифы OpenType")  

 Орнаменты часто используются как декоративные элементы в коротких фразах, таких как объявления о событиях. В следующем тексте орнаменты используются для выделения прописных букв названия события.  
  
 ![Текст, использующий каллиграфические символы OpenType](./media/opentype-font-features/opentype-swashes.gif "Текст, использующий каллиграфические символы OpenType")  
  
 В следующем примере разметки показано, как определить глифы для шрифта с помощью свойств <xref:System.Windows.Documents.Typography> объекта.  
  
 [!code-xaml[OpenTypeFontSamples#7](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#7)]  
  
### <a name="contextual-swashes"></a>Контекстные орнаментированные глифы  
 Некоторые комбинации орнаментированных глифов могут приводить к непривлекательному результату, например когда перекрываются подстрочные элементы на соседних буквах. Контекстные орнаментированные глифы позволяют использовать замещающий орнаментированный глиф, улучшающий внешний вид. Следующий текст показывает одно и то же слово до и после применения контекстного орнаментированного глифа.  
  
 ![Текст, использующий контекстные глифы OpenType](./media/opentype-font-features/opentype-contextual-swashes.gif "Текст, использующий контекстные глифы OpenType")  
  
 В следующем примере разметки показано, как определить контекстные шлейфы для шрифта Pescadero с помощью свойств <xref:System.Windows.Documents.Typography> объекта.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet16](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet16)]  
  
<a name="alternates"></a>   
## <a name="alternates"></a>Варианты  
 Варианты — это глифы, на которые может заменяться стандартный глиф. Шрифты OpenType, например шрифт Pericles, используемый в следующих примерах, могут содержать альтернативные глифы, которые можно использовать для создания различных представлений текста. Следующий текст демонстрирует стандартные глифы для шрифта Pericles.  
  
 ![Текст, использующий стандартные глифы OpenType](./media/opentype-font-features/opentype-standard-glyphs.gif "Текст, использующий стандартные глифы OpenType")  

 Шрифт OpenType Pericles содержит дополнительные глифы, предоставляющие стилистические варианты для стандартного набора глифов. Приведенный ниже текст отображает глифы с изменением стиля.  
  
 ![Текст, использующий стилистические альтернативные глифы OpenType](./media/opentype-font-features/opentype-stylistic-alternate-glyphs.gif "Текст, использующий стилистические альтернативные глифы OpenType")  
  
 В следующем примере разметки показано, как определить стилистические альтернативные глифы для шрифта Pericles с помощью свойств <xref:System.Windows.Documents.Typography> объекта.  
  
 [!code-xaml[OpenTypeFontSamples#2](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#2)]  
  
 Следующий текст демонстрирует несколько других стилистических вариантов глифов для шрифта Pericles.  
  
 ![Текст, использующий стилистические альтернативные глифы OpenType для шрифта Pericles](./media/opentype-font-features/opentype-stylistic-alternate-glyphs-pericles.gif "Текст, использующий стилистические альтернативные глифы OpenType для шрифта Pericles")

 В следующем примере разметки показано, как определяются эти другие стилистические варианты глифов.  
  
 [!code-xaml[OpenTypeFontSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#3)]  
  
### <a name="random-contextual-alternates"></a>Случайные контекстные варианты  
 Случайные контекстные варианты предоставляют несколько заменяющих глифов для одного символа. При реализации со шрифтами рукописного типа эта функция может имитировать рукописный ввод, используя набор случайно выбранных глифов с незначительными различиями во внешнем виде. В следующем тексте используются случайные контекстные варианты глифов для шрифта Lindsey. Обратите внимание, что буква «a» немного отличается.  
  
 ![Текст, использующий случайные контекстные варианты OpenType](./media/opentype-font-features/opentype-random-contextual-alternates.gif "Текст, использующий случайные контекстные варианты OpenType")  
  
 В следующем примере разметки показано, как определить Случайные контекстные альтернативы для шрифта Lindsey, используя свойства <xref:System.Windows.Documents.Typography> объекта.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet20](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet20)]  
  
### <a name="historical-forms"></a>Исторические формы  
 Исторические формы — это типографские соглашения, которые были приняты в прошлом. Следующий текст отображает фразу Boston, Massachusetts с помощью исторической формы глифов для шрифта Palatino Linotype.  
  
 ![Текст, использующий исторические формы OpenType](./media/opentype-font-features/opentype-historical-forms.gif "Текст, использующий исторические формы OpenType")  
   
 В следующем примере разметки показано, как определить исторические формы для шрифта Palatino Linotype с помощью свойств <xref:System.Windows.Documents.Typography> объекта.  
  
 [!code-xaml[OpenTypeFontSamples#8](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#8)]  
  
<a name="numerical_styles"></a>   
## <a name="numerical-styles"></a>Числовые стили  
 Шрифты OpenType поддерживают большое количество функций, которые могут использоваться с числовыми значениями в тексте.  
  
### <a name="fractions"></a>Дроби  
 Шрифты OpenType поддерживают стили для дробей, включая косую черту и накопление.  
  
 Следующий текст демонстрирует стили дробей для шрифта Palatino Linotype.  
  
 ![Текст, использующий косые черты OpenType и части с накоплением](./media/opentype-font-features/opentype-slashed-stacked-fractions.gif "Текст, использующий косые черты OpenType и части с накоплением")  
   
 В следующем примере разметки показано, как определить стили дробей для шрифта Palatino Linotype с помощью свойств <xref:System.Windows.Documents.Typography> объекта.  
  
 [!code-xaml[OpenTypeFontSamples#10](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#10)]  
  
### <a name="old-style-numerals"></a>Числа в старом стиле  
 Шрифты OpenType поддерживают формат чисел старого стиля. Этот формат используется для отображения чисел в стилях, которые уже не являются стандартными. Следующий текст демонстрирует дату 18 века в стандартном формате и в формате старого стиля для шрифта Palatino Linotype.  
  
 ![Текст, использующий цифры OpenType старого стиля](./media/opentype-font-features/opentype-old-style-numerals.gif "Текст, использующий цифры OpenType старого стиля")  
    
 Следующий текст демонстрирует стандартные числа и числа в старом стиле для шрифта Palatino Linotype.  
  
 ![Текст, использующий наборы чисел старого стиля OpenType](./media/opentype-font-features/opentype-old-style-numeral-sets.gif "Текст, использующий наборы чисел старого стиля OpenType")  
  
 В следующем примере разметки показано, как определить старые цифры стиля для шрифта Palatino Linotype с помощью свойств <xref:System.Windows.Documents.Typography> объекта.  
  
 [!code-xaml[OpenTypeFontSamples#11](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#11)]  
  
### <a name="proportional-and-tabular-figures"></a>Пропорциональные и табличные цифры  
 Шрифты OpenType поддерживают функцию пропорционального и табличного рисунка для управления выравниванием ширины при использовании цифр. При использовании пропорциональных цифр каждая цифра имеет свою ширину — например 1 будет уже, чем 5. Табличные цифры имеют одинаковую ширину, поэтому их можно выравнивать по вертикали, что повышает удобочитаемость финансовой информации.  
  
 В первом столбце следующего текста показаны два числа, использующие пропорциональные цифры и шрифт Miramonte. Обратите внимание на разную ширину цифр 5 и 1. Во втором столбце показаны те же два числа, ширина которых скорректирована с помощью функции табличных цифр.  
  
 ![Текст, использующий пропорциональные & Табличные цифры OpenType](./media/opentype-font-features/opentype-proportional-tabular-figures.gif "Текст, использующий пропорциональные и табличные цифры OpenType")  
    
 В следующем примере разметки показано, как определить пропорциональные и табличные цифры для шрифта Miramonte с помощью свойств <xref:System.Windows.Documents.Typography> объекта.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet19](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet19)]  
  
### <a name="slashed-zero"></a>Перечеркнутый нуль  
 Шрифты OpenType поддерживают формат чисел с косой чертой ноль, чтобы подчеркнуть разницу между буквой "O" и цифрой "0". Числа с перечеркнутым нулем часто используются для идентификаторов в финансовых и деловых сведениях.  
  
 Следующий текст демонстрирует пример идентификатора заказа с использованием шрифта Miramonte. В первой строке используются стандартные цифры. Во второй строке используются перечеркнутые нули для лучшего контраста с прописной буквой O.  
  
 ![Текст, в котором используются цифры OpenType, начинающиеся с косой черты](./media/opentype-font-features/opentype-slashed-zero-numerals.gif "Текст, в котором используются цифры OpenType, начинающиеся с косой черты")  
    
 В следующем примере разметки показано, как определить ноль цифр для шрифта Miramonte, используя свойства <xref:System.Windows.Documents.Typography> объекта.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet15](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet15)]  
  
<a name="typography_class"></a>   
## <a name="typography-class"></a>Класс Typography  
 <xref:System.Windows.Documents.Typography> Объект предоставляет набор функций, поддерживаемых шрифтом OpenType. Устанавливая свойства <xref:System.Windows.Documents.Typography> в разметке, можно легко создавать документы, использующие преимущества функций OpenType.  
  
 Следующий текст демонстрирует стандартные прописные буквы, буквы в стиле SmallCaps и в стиле AllSmallCaps для шрифта Pescadero. В данном случае для всех трех слов используется один и тот же размер шрифта.  
  
 ![Текст, использующий прописные буквы OpenType](./media/opentype-font-features/opentype-capitals.gif "Текст, использующий прописные буквы OpenType")  
    
 В следующем примере разметки показано, как определить прописные буквы для шрифта Pescadero с помощью свойств <xref:System.Windows.Documents.Typography> объекта. При использовании формата SmallCaps начальные прописные буквы игнорируются.  
  
 [!code-xaml[OpenTypeFontSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
 Следующий пример кода выполняет ту же задачу, что и предыдущий пример разметки.  
  
 [!code-csharp[TypographyCodeSnippets#TypographyCodeSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TypographyCodeSnippets/CSharp/Page1.xaml.cs#typographycodesnippet1)]
 [!code-vb[TypographyCodeSnippets#TypographyCodeSnippet1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TypographyCodeSnippets/visualbasic/page1.xaml.vb#typographycodesnippet1)]  
  
### <a name="typography-class-properties"></a>Свойства класса Typography  
 В следующей таблице перечислены свойства, значения и параметры по умолчанию для <xref:System.Windows.Documents.Typography> объекта.  
  
|Свойство.|Значения|Значение по умолчанию|  
|--------------|----------------|-------------------|  
|<xref:System.Windows.Documents.Typography.AnnotationAlternates%2A>|Числовое значение — байт|0|  
|<xref:System.Windows.Documents.Typography.Capitals%2A>|<xref:System.Windows.FontCapitals.AllPetiteCaps> &#124; <xref:System.Windows.FontCapitals.AllSmallCaps> &#124; <xref:System.Windows.FontCapitals.Normal> &#124; <xref:System.Windows.FontCapitals.PetiteCaps> &#124; <xref:System.Windows.FontCapitals.SmallCaps> &#124; <xref:System.Windows.FontCapitals.Titling> &#124; <xref:System.Windows.FontCapitals.Unicase>|<xref:System.Windows.FontCapitals.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.CapitalSpacing%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.CaseSensitiveForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.ContextualAlternates%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualLigatures%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualSwashes%2A>|Числовое значение — байт|0|  
|<xref:System.Windows.Documents.Typography.DiscretionaryLigatures%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.EastAsianExpertForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.EastAsianLanguage%2A>|<xref:System.Windows.FontEastAsianLanguage.HojoKanji> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis04> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis78> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis83> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis90> &#124; <xref:System.Windows.FontEastAsianLanguage.NlcKanji> &#124; <xref:System.Windows.FontEastAsianLanguage.Normal> &#124; <xref:System.Windows.FontEastAsianLanguage.Simplified> &#124; <xref:System.Windows.FontEastAsianLanguage.Traditional> &#124; <xref:System.Windows.FontEastAsianLanguage.TraditionalNames>|<xref:System.Windows.FontEastAsianLanguage.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.EastAsianWidths%2A>|<xref:System.Windows.FontEastAsianWidths.Full> &#124; <xref:System.Windows.FontEastAsianWidths.Half> &#124; <xref:System.Windows.FontEastAsianWidths.Normal> &#124; <xref:System.Windows.FontEastAsianWidths.Proportional> &#124; <xref:System.Windows.FontEastAsianWidths.Quarter> &#124; <xref:System.Windows.FontEastAsianWidths.Third>|<xref:System.Windows.FontEastAsianWidths.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.Fraction%2A>|<xref:System.Windows.FontFraction.Normal> &#124; <xref:System.Windows.FontFraction.Slashed> &#124; <xref:System.Windows.FontFraction.Stacked>|<xref:System.Windows.FontFraction.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.HistoricalForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.HistoricalLigatures%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.Kerning%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.MathematicalGreek%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.NumeralAlignment%2A>|<xref:System.Windows.FontNumeralAlignment.Normal> &#124; <xref:System.Windows.FontNumeralAlignment.Proportional> &#124; <xref:System.Windows.FontNumeralAlignment.Tabular>|<xref:System.Windows.FontNumeralAlignment.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.NumeralStyle%2A>|<xref:System.Boolean>|<xref:System.Windows.FontNumeralStyle.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.SlashedZero%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StandardLigatures%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.StandardSwashes%2A>|Числовое значение — байт|0|  
|<xref:System.Windows.Documents.Typography.StylisticAlternates%2A>|Числовое значение — байт|0|  
|<xref:System.Windows.Documents.Typography.StylisticSet1%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet2%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet3%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet4%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet5%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet6%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet7%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet8%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet9%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet10%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet11%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet12%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet13%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet14%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet15%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet16%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet17%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet18%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet19%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet20%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.Variants%2A>|<xref:System.Windows.FontVariants.Inferior> &#124; <xref:System.Windows.FontVariants.Normal> &#124; <xref:System.Windows.FontVariants.Ordinal> &#124; <xref:System.Windows.FontVariants.Ruby> &#124; <xref:System.Windows.FontVariants.Subscript> &#124; <xref:System.Windows.FontVariants.Superscript>|<xref:System.Windows.FontVariants.Normal?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>См. также

- <xref:System.Windows.Documents.Typography>
- [Спецификация OpenType](https://go.microsoft.com/fwlink/?LinkId=96731)
- [Оформление в WPF](typography-in-wpf.md)
- [Пакет образцов шрифтов OpenType](sample-opentype-font-pack.md)
- [Упаковка шрифтов с приложениями](packaging-fonts-with-applications.md)
