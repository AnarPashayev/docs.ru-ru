---
title: Добавление экрана-заставки
description: Узнайте, как добавить окно запуска или экран-заставку в приложение Windows Presentation Foundation (WPF).
ms.date: 08/18/2018
helpviewer_keywords:
- WPF [WPF], splash screen
- startup window [WPF]
- SplashScreen class [WPF]
- splash screen [WPF]
ms.assetid: d70a25c4-5fb9-4c27-b01d-b1b8ef39b3fd
ms.openlocfilehash: 0d0cf2e2a550320650c3b4a0c257071a0403c32b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617964"
---
# <a name="how-to-add-a-splash-screen-to-a-wpf-application"></a>Практическое руководство. Добавление в WPF-приложение экрана-заставки

В этом разделе показано, как добавить окно запуска или *экран-заставку*в приложение Windows Presentation Foundation (WPF).

## <a name="to-add-an-existing-image-as-a-splash-screen"></a>Добавление существующего изображения в качестве экрана-заставки

1. Создайте или найдите изображение, которое вы хотите использовать для экрана-заставки. Можно использовать любой формат изображения, поддерживаемый компонентом Windows Imaging Component (WIC). Например, можно использовать формат BMP, GIF, JPEG, PNG или TIFF.

2. Добавьте файл изображения в проект приложения WPF.

3. В **Обозреватель решений**выберите изображение.

4. В окно свойств щелкните стрелку раскрывающегося списка для свойства **действие сборки** .

5. Выберите **SplashScreen** из раскрывающегося списка.

6. Нажмите клавишу **F5** , чтобы создать и запустить приложение.

     Изображение экрана-заставки отображается в центре экрана, а затем исчезает при появлении главного окна приложения.

## <a name="to-exclude-the-splash-screen-from-build"></a>Исключение экрана-заставки из сборки

1. В **Обозреватель решений**выберите изображение экрана-заставки.

2. В окне **Свойства** задайте для **действия сборки** значение **нет**.

## <a name="to-remove-the-splash-screen-from-an-application"></a>Удаление экрана-заставки из приложения

В **Обозреватель решений**удалите изображение экрана-заставки.

## <a name="see-also"></a>См. также

- <xref:System.Windows.SplashScreen>
- [Как добавить существующие элементы в проект](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))
