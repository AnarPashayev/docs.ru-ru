---
title: Практическое руководство. Проверка данных в элементе управления DataGridView в Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [Windows Forms], validation
- DataGridView control [Windows Forms], data validation
- data grids [Windows Forms], validating data
- data validation [Windows Forms], Windows Forms
ms.assetid: d10aef35-701e-4a3c-a684-2a2ed1aeaca6
ms.openlocfilehash: 12fd668e22703271f8c629baf56487dd084cfd8b
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591029"
---
# <a name="how-to-validate-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="604b3-102">Практическое руководство. Проверка данных в элементе управления DataGridView в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="604b3-102">How to: Validate Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="604b3-103">В следующем примере кода показано, как проверить данные, введенные пользователем в элемент управления <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="604b3-103">The following code example demonstrates how to validate data entered by a user into a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="604b3-104">В этом примере <xref:System.Windows.Forms.DataGridView> заполняется строками из таблицы `Customers` образца базы данных "Northwind".</span><span class="sxs-lookup"><span data-stu-id="604b3-104">In this example, the <xref:System.Windows.Forms.DataGridView> is populated with rows from the `Customers` table of the Northwind sample database.</span></span> <span data-ttu-id="604b3-105">При редактировании ячейки в столбце `CompanyName` проверяется, что ее значение не является пустым.</span><span class="sxs-lookup"><span data-stu-id="604b3-105">When the user edits a cell in the `CompanyName` column, its value is tested for validity by checking that it is not empty.</span></span> <span data-ttu-id="604b3-106">Если обработчик события для <xref:System.Windows.Forms.DataGridView.CellValidating> обнаружит, что значение является пустой строкой, то <xref:System.Windows.Forms.DataGridView> запрещает пользователю выход из ячейки до введения непустой строки.</span><span class="sxs-lookup"><span data-stu-id="604b3-106">If the event handler for the <xref:System.Windows.Forms.DataGridView.CellValidating> event finds that the value is an empty string, the <xref:System.Windows.Forms.DataGridView> prevents the user from exiting the cell until a non-empty string is entered.</span></span>  
  
 <span data-ttu-id="604b3-107">Полное описание этого примера кода, см. в разделе [Пошаговое руководство: Проверка данных в Windows Forms элемента управления DataGridView](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="604b3-107">For a complete explanation of this code example, see [Walkthrough: Validating Data in the Windows Forms DataGridView Control](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="604b3-108">Пример</span><span class="sxs-lookup"><span data-stu-id="604b3-108">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewDataValidation#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="604b3-109">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="604b3-109">Compiling the Code</span></span>  
 <span data-ttu-id="604b3-110">Для этого примера требуются:</span><span class="sxs-lookup"><span data-stu-id="604b3-110">This example requires:</span></span>  
  
- <span data-ttu-id="604b3-111">ссылки на сборки System, System.Data, System.Windows.Forms и System.XML.</span><span class="sxs-lookup"><span data-stu-id="604b3-111">References to the System, System.Data, System.Windows.Forms and System.XML assemblies.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="604b3-112">Безопасность платформы .NET Framework</span><span class="sxs-lookup"><span data-stu-id="604b3-112">.NET Framework Security</span></span>  
 <span data-ttu-id="604b3-113">Хранение конфиденциальных сведений (например, пароля) в строке подключения может повлиять на безопасность приложения.</span><span class="sxs-lookup"><span data-stu-id="604b3-113">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="604b3-114">Использование проверки подлинности Windows (также называемой встроенными средствами безопасности) — более безопасный способ управления доступом к базе данных.</span><span class="sxs-lookup"><span data-stu-id="604b3-114">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="604b3-115">Дополнительные сведения см. в разделе [Защита сведений о подключении](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="604b3-115">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="604b3-116">См. также</span><span class="sxs-lookup"><span data-stu-id="604b3-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="604b3-117">Пошаговое руководство: Проверка данных в элементе управления DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="604b3-117">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="604b3-118">Ввод данных с помощью элемента управления DataGridView в Windows Forms</span><span class="sxs-lookup"><span data-stu-id="604b3-118">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="604b3-119">Пошаговое руководство: Обработка ошибок, возникающих во время ввода данных в элементе управления DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="604b3-119">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [<span data-ttu-id="604b3-120">Защита сведений о подключении</span><span class="sxs-lookup"><span data-stu-id="604b3-120">Protecting Connection Information</span></span>](../../data/adonet/protecting-connection-information.md)
