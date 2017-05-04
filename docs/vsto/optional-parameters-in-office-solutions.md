---
title: "Необязательные параметры в решениях Office | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "разработка приложений [разработка решений Office в Visual Studio], необязательные параметры"
  - "отсутствующее поле [разработка решений Office в Visual Studio]"
  - "Office - приложения [разработка решений Office в Visual Studio], необязательные параметры"
  - "необязательные параметры [разработка решений Office в Visual Studio]"
  - "параметры [разработка решений Office в Visual Studio], необязательные"
  - "Visual Basic [разработка решений Office в Visual Studio], необязательные параметры"
  - "Visual C# [разработка решений Office в Visual Studio], необязательные параметры"
ms.assetid: 109eaef6-08bb-4b59-a29e-921f856027cc
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# Необязательные параметры в решениях Office
  Многие методы в объектных моделях приложений Microsoft Office принимают необязательные параметры.  При использовании Visual Basic для разработки решения Office в Visual Studio значение для необязательных параметров передавать не нужно, так как для каждого отсутствующего параметра автоматически используется значение по умолчанию.  В большинстве случаев в проектах Visual C\# также можно опускать необязательные параметры. Однако в проектах Word на уровне документа необязательные параметры **ref** класса `ThisDocument` опускать нельзя.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Дополнительные сведения о работе с необязательными параметрами в проектах Visual C\# и Visual Basic см. в статьях [Именованные и необязательные аргументы &#40;Руководство по программированию на C&#35;&#41;](/dotnet/csharp/programming-guide/classes-and-structs/named-and-optional-arguments) и [Необязательные параметры &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters).  
  
> [!NOTE]  
>  В более ранних версиях Visual Studio в проектах Visual C\# необходимо было передавать значение для каждого необязательного параметра.  Для удобства эти проекты содержат глобальную переменную с именем `missing`, которую можно передавать в необязательный параметр, если для него нужно использовать значение по умолчанию.  Проекты Visual C\# для Office в Visual Studio все еще содержат переменную `missing`, но ее обычно не требуется использовать при разработке решений Office в [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], за исключением вызова методов с необязательными параметрами **ref** в классе `ThisDocument` в проектах на уровне документа для Word.  
  
## Пример в Excel  
 Метод <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> имеет много необязательных параметров.  Как показано в следующем примере кода, для одних параметров можно указать значения, а для других — принять значение по умолчанию.  В этом примере требуется проект на уровне документа с классом листа под именем `Sheet1`.  
  
 [!code-csharp[Trin_VstrefGeneralExcel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstrefGeneralExcel/CS/Sheet1.cs#1)]
 [!code-vb[Trin_VstrefGeneralExcel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstrefGeneralExcel/VB/Sheet1.vb#1)]  
  
## Пример в Word  
 Метод <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> имеет много необязательных параметров.  Как показано в следующем примере кода, для одних параметров можно указать значения, а для других — принять значение по умолчанию.  
  
 [!code-csharp[Trin_VstrefGeneralWord#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstrefGeneralWord/CS/ThisDocument.cs#1)]
 [!code-vb[Trin_VstrefGeneralWord#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstrefGeneralWord/VB/ThisDocument.vb#1)]  
  
## Использование необязательных параметров методов в классе ThisDocument в проектах на уровне документа Visual C\# для Word  
 Объектная модель Word содержит много методов с необязательными параметрами **ref**, которые принимают значения <xref:System.Object>.  Однако в проектах на уровне документа Visual C\# для Word нельзя опускать необязательные параметры **ref** методов созданного класса `ThisDocument`.  Visual C\# позволяет опускать необязательные параметры **ref** только для методов интерфейсов, но не классов.  Например, в следующем примере код не компилируется, так как нельзя опускать необязательные параметры **ref** метода <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> класса `ThisDocument`.  
  
 [!code-csharp[Trin_VstrefGeneralWord#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstrefGeneralWord/CS/ThisDocument.cs#3)]  
  
 При вызове методов класса `ThisDocument` следуйте приведенным ниже рекомендациям:  
  
-   Чтобы принять значение по умолчанию необязательного параметра **ref**, передайте в параметр переменную `missing`.  Переменная `missing` автоматически определяется в проектах Visual C\# для Office, и ей назначается значение <xref:System.Type.Missing> в созданном коде проекта.  
  
-   Чтобы указать собственное значение для необязательного параметра **ref**, объявите объект, назначаемый значению, которое вы хотите указать, а затем передайте этот объект в параметр.  
  
 В следующем примере кода показано, как вызвать метод <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> путем указания значения для параметра *ignoreUppercase* и принятия значения по умолчанию для других параметров.  
  
 [!code-csharp[Trin_VstrefGeneralWord#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstrefGeneralWord/CS/ThisDocument.cs#4)]  
  
 Если требуется написать код, который опускает необязательные параметры **ref** метода в классе `ThisDocument`, также можно вызвать тот же самый метод для объекта <xref:Microsoft.Office.Interop.Word.Document>, возвращаемого свойством <xref:Microsoft.Office.Tools.Word.Document.InnerObject%2A>, и опустить параметры из данного метода.  Это можно сделать, так как <xref:Microsoft.Office.Interop.Word.Document> — интерфейс, а не класс.  
  
 [!code-csharp[Trin_VstrefGeneralWord#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstrefGeneralWord/CS/ThisDocument.cs#5)]  
  
 Дополнительные сведения о параметрах типов значений и ссылочных типов см. в статьях [Передача аргументов по значению и по ссылке &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) \(для Visual Basic\) и [Передача параметров &#40;Руководство по программированию в C&#35;&#41;](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).  
  
## См. также  
 [Разработка решений Office](../vsto/developing-office-solutions.md)   
 [Написание кода в решениях Office](../vsto/writing-code-in-office-solutions.md)  
  
  