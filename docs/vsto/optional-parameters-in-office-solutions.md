---
title: "Необязательные параметры в решениях Office | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], optional parameters
- Visual C# [Office development in Visual Studio], optional parameters
- Visual Basic [Office development in Visual Studio], optional parameters
- application development [Office development in Visual Studio], optional parameters
- missing field [Office development in Visual Studio]
- optional parameters [Office development in Visual Studio]
- parameters [Office development in Visual Studio], optional
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: fe40b6bc0af9df294408079c8a27dfac42df97b0
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="optional-parameters-in-office-solutions"></a>Необязательные параметры в решениях Office
  Многие методы в объектных моделях приложений Microsoft Office принимают необязательные параметры. При использовании Visual Basic для разработки решения Office в Visual Studio значение для необязательных параметров передавать не нужно, так как для каждого отсутствующего параметра автоматически используется значение по умолчанию. В большинстве случаев можно также опустить необязательные параметры в проектах Visual C#. Тем не менее, нельзя опускать необязательные **ref** параметры `ThisDocument` классов в проектах уровня документа Word.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Дополнительные сведения о работе с необязательными параметрами в проектах Visual C# и Visual Basic см. в разделе [&#40; именованные и необязательные аргументы И &#35; Руководство по программированию &#41; ](/dotnet/csharp/programming-guide/classes-and-structs/named-and-optional-arguments) и [необязательные параметры &#40; Visual Basic &#41; ](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters).  
  
> [!NOTE]  
>  В более ранних версиях Visual Studio в проектах Visual C# необходимо было передавать значение для каждого необязательного параметра. Для удобства эти проекты содержат глобальную переменную с именем `missing`, которую можно передавать в необязательный параметр, если для него нужно использовать значение по умолчанию. Проекты Visual C# для Office в Visual Studio по-прежнему включить `missing` переменной, но обычно не требуется использовать его при разработке решений Office в [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], за исключением того, при вызове методов с необязательными **ref** параметры в `ThisDocument` классов в проектах уровня документа для Word.  
  
## <a name="example-in-excel"></a>Пример в Excel  
 Метод <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> имеет много необязательных параметров. Как показано в следующем примере кода, для одних параметров можно указать значения, а для других — принять значение по умолчанию. В этом примере требуется проект на уровне документа с классом листа под именем `Sheet1`.  
  
 [!code-csharp[Trin_VstrefGeneralExcel#1](../vsto/codesnippet/CSharp/excelworkbook1/Sheet1.cs#1)]
 [!code-vb[Trin_VstrefGeneralExcel#1](../vsto/codesnippet/VisualBasic/excelworkbook1/Sheet1.vb#1)]  
  
## <a name="example-in-word"></a>Пример в Word  
 Метод <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> имеет много необязательных параметров. Как показано в следующем примере кода, для одних параметров можно указать значения, а для других — принять значение по умолчанию.  
  
 [!code-vb[Trin_VstrefGeneralWord#1](../vsto/codesnippet/VisualBasic/worddocument1/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstrefGeneralWord#1](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#1)]  
  
## <a name="using-optional-parameters-of-methods-in-the-thisdocument-class-in-visual-c-document-level-projects-for-word"></a>Использование необязательных параметров методов в классе ThisDocument в проектах на уровне документа Visual C# для Word  
 Объектная модель Word содержит много методов с необязательными **ref** параметры, которые принимают <xref:System.Object> значения. Тем не менее, нельзя опускать необязательные **ref** параметров методов созданного `ThisDocument` классов в проектах уровня документа Visual C# для Word. Visual C# позволяет опускать необязательные **ref** параметры только для методов интерфейсов, не классов. Например, приведенный ниже код не компилируется, так как нельзя опускать необязательные **ref** параметры <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> метод `ThisDocument` класса.  
  
 [!code-csharp[Trin_VstrefGeneralWord#3](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#3)]  
  
 При вызове методов класса `ThisDocument` следуйте приведенным ниже рекомендациям:  
  
-   Чтобы принять значение по умолчанию для дополнительного **ref** параметра, передайте `missing` в параметр переменную. Переменная `missing` автоматически определяется в проектах Visual C# для Office, и ей назначается значение <xref:System.Type.Missing> в созданном коде проекта.  
  
-   Чтобы указать собственное значение для дополнительного **ref** параметр, объявите объект, присваивается значение, которое вы хотите указать и затем передайте этот объект в параметр.  
  
 В следующем примере кода показано, как вызвать <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> метод, указав значение для *ignoreUppercase* параметра и принятие значений по умолчанию для остальных параметров.  
  
 [!code-csharp[Trin_VstrefGeneralWord#4](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#4)]  
  
 Если требуется написать код, который опускает необязательные **ref** параметров метода в `ThisDocument` класса, также можно вызвать тот же метод на <xref:Microsoft.Office.Interop.Word.Document> объект, возвращаемый <xref:Microsoft.Office.Tools.Word.Document.InnerObject%2A> свойство и опустить параметры из этого метода. Это можно сделать, так как <xref:Microsoft.Office.Interop.Word.Document> — интерфейс, а не класс.  
  
 [!code-csharp[Trin_VstrefGeneralWord#5](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#5)]  
  
 Дополнительные сведения о параметрах типов значений и ссылочных типов см. в разделе [передача аргументов по значению и по ссылку &#40; Visual Basic &#41; ](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) (для Visual Basic) и [передача параметров &#40; И &#35; Руководство по программированию &#41; ](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).  
  
## <a name="see-also"></a>См. также  
 [Разработка решений Office](../vsto/developing-office-solutions.md)   
 [Writing Code in Office Solutions](../vsto/writing-code-in-office-solutions.md)  
  
  