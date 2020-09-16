---
title: Практическое руководство. Связывание объекта DataView с элементом управления DataGridView в Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b73d60a-6049-446a-85a7-3e5a68b183e2
ms.openlocfilehash: cbae5453be485896e27a5039ece20bb3bcec9913
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556984"
---
# <a name="how-to-bind-a-dataview-object-to-a-windows-forms-datagridview-control"></a>Практическое руководство. Связывание объекта DataView с элементом управления DataGridView в Windows Forms
Элемент управления <xref:System.Windows.Forms.DataGridView> предоставляет мощный и гибкий способ отображения данных в табличном формате. Элемент управления <xref:System.Windows.Forms.DataGridView> поддерживает стандартную модель привязки данных Windows Forms, поэтому он выполняет привязку к <xref:System.Data.DataView> и другим различным источникам данных. Однако в большинстве случаев выполняется привязка к компоненту <xref:System.Windows.Forms.BindingSource>, управляющему взаимодействием с источником данных.  
  
 Дополнительные сведения об <xref:System.Windows.Forms.DataGridView> элементе управления см. в разделе [Общие сведения о элементе управления DataGridView](/dotnet/desktop/winforms/controls/datagridview-control-overview-windows-forms).  
  
### <a name="to-connect-a-datagridview-control-to-a-dataview"></a>Соединение элемента управления DataGridView с объектом DataView  
  
1. Реализуйте метод, обрабатывающий получение данных из базы данных. В следующем примере реализован метод `GetData`, инициализирующий компонент <xref:System.Data.SqlClient.SqlDataAdapter> и использующий его для заполнения объекта <xref:System.Data.DataSet>. Убедитесь, что переменной `connectionString` присвоено значение, соответствующее базе данных. Потребуется доступ к SQL Server с установленным образцом базы данных AdventureWorks.  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1getdata)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1getdata)]  
  
2. В обработчике событий <xref:System.Windows.Forms.Form.Load> формы привяжите элемент управления <xref:System.Windows.Forms.DataGridView> к компоненту <xref:System.Windows.Forms.BindingSource> и вызовите метод `GetData` для получения данных из базы данных. Объект <xref:System.Data.DataView> создается из LINQ to DataSet запроса к контакту <xref:System.Data.DataTable> и затем привязывается к <xref:System.Windows.Forms.BindingSource> компоненту.  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1formload)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1formload)]  
  
## <a name="see-also"></a>См. также

- [Привязка данных и LINQ to DataSet](data-binding-and-linq-to-dataset.md)
