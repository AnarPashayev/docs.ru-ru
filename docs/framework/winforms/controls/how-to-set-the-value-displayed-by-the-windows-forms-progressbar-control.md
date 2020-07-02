---
title: Установка значения, отображаемого элементом управления ProgressBar
description: Узнайте, как задать значение, отображаемое элементом управления Windows Forms ProgressBar. Существует несколько подходов, которые можно выбрать для использования.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ProgressBar control [Windows Forms], setting value displayed
- progress controls [Windows Forms], setting value displayed
ms.assetid: 0e5010ad-1e9a-4271-895e-5a3d24d37a26
ms.openlocfilehash: 75fe1b416636471d797a39134f45a05c972c9d39
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618107"
---
# <a name="how-to-set-the-value-displayed-by-the-windows-forms-progressbar-control"></a>Практическое руководство. Установка значения, отображаемого c помощью элемента управления ProgressBar в Windows Forms
> [!IMPORTANT]
> Элемент управления <xref:System.Windows.Forms.ToolStripProgressBar> заменяет элемент управления <xref:System.Windows.Forms.ProgressBar> и расширяет его функциональные возможности; однако при необходимости элемент управления <xref:System.Windows.Forms.ProgressBar> можно сохранить для обратной совместимости и использования в будущем.  
  
 .NET Framework предоставляет несколько различных способов отобразить заданное значение в <xref:System.Windows.Forms.ProgressBar> элементе управления. Выбор способа зависит от поставленной задачи или от решаемой проблемы. В следующей таблице показаны подходы, которые можно выбрать.  
  
|Подход|Описание|  
|--------------|-----------------|  
|Задайте значение <xref:System.Windows.Forms.ProgressBar> элемента управления напрямую.|Этот подход удобен для задач, где известно общее количество элементов, которые будут задействованы, например чтение записей из источника данных. Кроме того, если необходимо задать значение только один раз или дважды, это легко сделать. Наконец, используйте этот процесс, если необходимо уменьшить значение, отображаемое индикатором выполнения.|  
|Увеличьте <xref:System.Windows.Forms.ProgressBar> Отображаемое значение на фиксированное.|Этот подход удобен при отображении простого счетчика между минимальным и максимальным значением, например прошедшее время или числом файлов, которые были обработаны из известного итога.|  
|Увеличьте <xref:System.Windows.Forms.ProgressBar> Отображаемое значение, используя различные значения.|Этот подход удобен, если необходимо изменить отображаемое значение на несколько раз в разных объемах. Пример показывает объем занятого места на жестком диске при записи ряда файлов на диск.|  
  
 Самым прямым способом задания значения, отображаемого индикатором выполнения, является установка <xref:System.Windows.Forms.ProgressBar.Value%2A> Свойства. Это можно сделать либо во время разработки, либо во время выполнения.  
  
### <a name="to-set-the-progressbar-value-directly"></a>Установка значения ProgressBar напрямую  
  
1. Задайте <xref:System.Windows.Forms.ProgressBar> значения элемента управления <xref:System.Windows.Forms.ProgressBar.Minimum%2A> и <xref:System.Windows.Forms.ProgressBar.Maximum%2A> .  
  
2. В коде задайте для свойства элемента управления <xref:System.Windows.Forms.ProgressBar.Value%2A> целочисленное значение между минимальным и максимальным значениями, которые вы установили.  
  
    > [!NOTE]
    > Если задать <xref:System.Windows.Forms.ProgressBar.Value%2A> свойство вне границ <xref:System.Windows.Forms.ProgressBar.Minimum%2A> , установленных <xref:System.Windows.Forms.ProgressBar.Maximum%2A> свойствами и, элемент управления создаст <xref:System.ArgumentException> исключение.  
  
     В следующем примере кода показано, как задать <xref:System.Windows.Forms.ProgressBar> значение напрямую. Код считывает записи из источника данных и обновляет индикатор выполнения и метку при каждом считывании записи данных. Этот пример требует, чтобы форма соработала <xref:System.Windows.Forms.Label> элемент управления, <xref:System.Windows.Forms.ProgressBar> элемент управления и таблицу данных со строкой `CustomerRow` с именами `FirstName` и `LastName` .  
  
    ```vb  
    Public Sub CreateNewRecords()  
       ' Sets the progress bar's Maximum property to  
       ' the total number of records to be created.  
       ProgressBar1.Maximum = 20  
  
       ' Creates a new record in the dataset.  
       ' NOTE: The code below will not compile, it merely  
       ' illustrates how the progress bar would be used.  
       Dim anyRow As CustomerRow = DatasetName.ExistingTable.NewRow  
       anyRow.FirstName = "Stephen"  
       anyRow.LastName = "James"  
       ExistingTable.Rows.Add(anyRow)  
  
       ' Increases the value displayed by the progress bar.  
       ProgressBar1.Value += 1  
       ' Updates the label to show that a record was read.  
       Label1.Text = "Records Read = " & ProgressBar1.Value.ToString()  
    End Sub  
    ```  
  
    ```csharp  
    public void createNewRecords()  
    {  
       // Sets the progress bar's Maximum property to  
       // the total number of records to be created.  
       progressBar1.Maximum = 20;  
  
       // Creates a new record in the dataset.  
       // NOTE: The code below will not compile, it merely  
       // illustrates how the progress bar would be used.  
       CustomerRow anyRow = DatasetName.ExistingTable.NewRow();  
       anyRow.FirstName = "Stephen";  
       anyRow.LastName = "James";  
       ExistingTable.Rows.Add(anyRow);  
  
       // Increases the value displayed by the progress bar.  
       progressBar1.Value += 1;  
       // Updates the label to show that a record was read.  
       label1.Text = "Records Read = " + progressBar1.Value.ToString();  
    }  
    ```  
  
     При отображении хода выполнения, который выполняется с фиксированным интервалом, можно задать значение и затем вызвать метод, который увеличивает <xref:System.Windows.Forms.ProgressBar> значение элемента управления на этот интервал. Это полезно для таймеров и других сценариев, в которых ход выполнения не измеряется в процентах от целого.  
  
### <a name="to-increase-the-progress-bar-by-a-fixed-value"></a>Увеличение индикатора выполнения на фиксированное значение  
  
1. Задайте <xref:System.Windows.Forms.ProgressBar> значения элемента управления <xref:System.Windows.Forms.ProgressBar.Minimum%2A> и <xref:System.Windows.Forms.ProgressBar.Maximum%2A> .  
  
2. Задайте <xref:System.Windows.Forms.ProgressBar.Step%2A> для свойства элемента управления целое число, представляющее величину, чтобы увеличить отображаемое значение индикатора выполнения.  
  
3. Вызовите <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> метод, чтобы изменить значение, отображаемое на величину, заданную в <xref:System.Windows.Forms.ProgressBar.Step%2A> свойстве.  
  
     В следующем примере кода показано, как индикатор выполнения может поддерживать количество файлов в операции копирования.  
  
     В следующем примере, когда каждый файл считывается в память, индикатор выполнения и метка обновляются для отражения общего числа считываемых файлов. В этом примере требуется, чтобы форма соработала <xref:System.Windows.Forms.Label> элемент управления и <xref:System.Windows.Forms.ProgressBar> элемент управления.  
  
    ```vb  
    Public Sub LoadFiles()  
       ' Sets the progress bar's minimum value to a number representing  
       ' no operations complete -- in this case, no files read.  
       ProgressBar1.Minimum = 0  
       ' Sets the progress bar's maximum value to a number representing  
       ' all operations complete -- in this case, all five files read.  
       ProgressBar1.Maximum = 5  
       ' Sets the Step property to amount to increase with each iteration.  
       ' In this case, it will increase by one with every file read.  
       ProgressBar1.Step = 1  
  
       ' Dimensions a counter variable.  
       Dim i As Integer  
       ' Uses a For...Next loop to iterate through the operations to be  
       ' completed. In this case, five files are to be copied into memory,  
       ' so the loop will execute 5 times.  
       For i = 0 To 4  
          ' Insert code to copy a file  
          ProgressBar1.PerformStep()  
          ' Update the label to show that a file was read.  
          Label1.Text = "# of Files Read = " & ProgressBar1.Value.ToString  
       Next i  
    End Sub  
    ```  
  
    ```csharp  
    public void loadFiles()  
    {  
       // Sets the progress bar's minimum value to a number representing  
       // no operations complete -- in this case, no files read.  
       progressBar1.Minimum = 0;  
       // Sets the progress bar's maximum value to a number representing  
       // all operations complete -- in this case, all five files read.  
       progressBar1.Maximum = 5;  
       // Sets the Step property to amount to increase with each iteration.  
       // In this case, it will increase by one with every file read.  
       progressBar1.Step = 1;  
  
       // Uses a for loop to iterate through the operations to be  
       // completed. In this case, five files are to be copied into memory,  
       // so the loop will execute 5 times.  
       for (int i = 0; i <= 4; i++)  
       {  
          // Inserts code to copy a file  
          progressBar1.PerformStep();  
          // Updates the label to show that a file was read.  
          label1.Text = "# of Files Read = " + progressBar1.Value.ToString();  
       }  
    }  
    ```  
  
     Наконец, можно увеличить значение, отображаемое индикатором выполнения, чтобы каждое увеличение было уникальным. Это полезно, если вы отслеживаете ряд уникальных операций, например запись файлов различных размеров на жесткий диск или измерение хода выполнения в процентах от целого.  
  
### <a name="to-increase-the-progress-bar-by-a-dynamic-value"></a>Увеличение индикатора выполнения на динамическое значение  
  
1. Задайте <xref:System.Windows.Forms.ProgressBar> значения элемента управления <xref:System.Windows.Forms.ProgressBar.Minimum%2A> и <xref:System.Windows.Forms.ProgressBar.Maximum%2A> .  
  
2. Вызовите <xref:System.Windows.Forms.ProgressBar.Increment%2A> метод, чтобы изменить значение, отображаемое указанным целым числом.  
  
     В следующем примере кода показано, как индикатор выполнения может вычислить, сколько места на диске использовалось во время операции копирования.  
  
     В следующем примере, когда каждый файл записывается на жесткий диск, индикатор выполнения и метка обновляются с учетом объема доступного места на жестком диске. В этом примере требуется, чтобы форма соработала <xref:System.Windows.Forms.Label> элемент управления и <xref:System.Windows.Forms.ProgressBar> элемент управления.  
  
    ```vb  
    Public Sub ReadFiles()  
       ' Sets the progress bar's minimum value to a number
       ' representing the hard disk space before the files are read in.  
       ' You will most likely have to set this using a system call.  
       ' NOTE: The code below is meant to be an example and  
       ' will not compile.  
       ProgressBar1.Minimum = AvailableDiskSpace()  
       ' Sets the progress bar's maximum value to a number
       ' representing the total hard disk space.  
       ' You will most likely have to set this using a system call.  
       ' NOTE: The code below is meant to be an example
       ' and will not compile.  
       ProgressBar1.Maximum = TotalDiskSpace()  
  
       ' Dimension a counter variable.  
       Dim i As Integer  
       ' Uses a For...Next loop to iterate through the operations to be  
       ' completed. In this case, five files are to be written to the disk,  
       ' so it will execute the loop 5 times.  
       For i = 1 To 5  
          ' Insert code to read a file into memory and update file size.  
          ' Increases the progress bar's value based on the size of
          ' the file currently being written.  
          ProgressBar1.Increment(FileSize)  
          ' Updates the label to show available drive space.  
          Label1.Text = "Current Disk Space Used = " &_
          ProgressBar1.Value.ToString()  
       Next i  
    End Sub  
    ```  
  
    ```csharp  
    public void readFiles()  
    {  
       // Sets the progress bar's minimum value to a number
       // representing the hard disk space before the files are read in.  
       // You will most likely have to set this using a system call.  
       // NOTE: The code below is meant to be an example and
       // will not compile.  
       progressBar1.Minimum = AvailableDiskSpace();  
       // Sets the progress bar's maximum value to a number
       // representing the total hard disk space.  
       // You will most likely have to set this using a system call.  
       // NOTE: The code below is meant to be an example
       // and will not compile.  
       progressBar1.Maximum = TotalDiskSpace();  
  
       // Uses a for loop to iterate through the operations to be  
       // completed. In this case, five files are to be written  
       // to the disk, so it will execute the loop 5 times.  
       for (int i = 1; i<= 5; i++)  
       {  
          // Insert code to read a file into memory and update file size.  
          // Increases the progress bar's value based on the size of
          // the file currently being written.  
          progressBar1.Increment(FileSize);  
          // Updates the label to show available drive space.  
          label1.Text = "Current Disk Space Used = " + progressBar1.Value.ToString();  
       }  
    }  
    ```  
  
## <a name="see-also"></a>См. также

- <xref:System.Windows.Forms.ProgressBar>
- <xref:System.Windows.Forms.ToolStripProgressBar>
- [Общие сведения об элементе управления ProgressBar](progressbar-control-overview-windows-forms.md)
- [Элемент управления ProgressBar](progressbar-control-windows-forms.md)
