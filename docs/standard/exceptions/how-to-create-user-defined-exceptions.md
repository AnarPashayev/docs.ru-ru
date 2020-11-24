---
title: Практическое руководство. Создание пользовательских исключений
description: Узнайте, как создавать пользовательские исключения, которые являются альтернативой иерархии классов исключений, производных от базового класса Exception в .NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- user-defined exceptions
- exceptions, examples
- exceptions, user-defined
ms.assetid: 25819a5a-f915-4fc8-b924-a76915674e04
ms.openlocfilehash: b0a8549c9bacf322a0685c7b505185ab1d1101f6
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828131"
---
# <a name="how-to-create-user-defined-exceptions"></a>Создание пользовательских исключений

Платформа .NET предоставляет иерархию классов исключений, производных от базового класса <xref:System.Exception>. Тем не менее, если ни одно из стандартных исключений не подходит, можно создать собственные классы исключений путем наследования от класса <xref:System.Exception>.

При создании собственных исключений заканчивайте имя класса пользовательского исключения словом Exception и реализуйте три общих конструктора, как показано в следующем примере. В примере определяется новый класс исключений `EmployeeListNotFoundException`. Этот класс является производным от <xref:System.Exception> и включает три конструктора.

[!code-cpp[dg_exceptionDesign#14](../../../samples/snippets/cpp/VS_Snippets_CLR/dg_exceptionDesign/cpp/example2.cpp#14)]
[!code-csharp[dg_exceptionDesign#14](../../../samples/snippets/csharp/VS_Snippets_CLR/dg_exceptionDesign/cs/example2.cs#14)]
[!code-vb[dg_exceptionDesign#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/dg_exceptionDesign/vb/example2.vb#14)]  

> [!NOTE]
> В ситуациях, когда используется удаленное взаимодействие, необходимо убедиться, что метаданные для пользовательского исключения доступны на сервере (вызываемый объект) и для клиента (прокси-объект или вызывающий объект). Дополнительные сведения см. в разделе [Лучшие методики обработки исключений](best-practices-for-exceptions.md).

## <a name="see-also"></a>См. также

- [Исключения](index.md)
