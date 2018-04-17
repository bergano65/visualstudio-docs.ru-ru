---
title: Позднее связывание в решениях Office | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- objects [Office development in Visual Studio], casting
- types [Office development in Visual Studio], casting
- automation [Office development in Visual Studio], casting objects
- casting, object to specific type
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7e205874e1c5c4e5de639e28768d6369b43c1e1a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="late-binding-in-office-solutions"></a>Позднее связывание в решениях Office
  Некоторые типы в объектных моделях приложений Office предоставляют функциональные возможности, доступные через компоненты позднего связывания. Например некоторые методы и свойства могут возвращать различные типы объектов в зависимости от контекста приложения Office, и некоторые типы могут предоставлять различные методы или свойства в различных контекстах.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Проекты Visual Basic, где **Option Strict** off и проектах, ориентированных на Visual C# [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] может работать непосредственно с типами, которые реализуют эти компоненты позднего связывания.  
  
## <a name="implicit-and-explicit-casting-of-object-return-values"></a>Неявное и явное приведение возвращаемых значений объекта  
 Многие методы и свойства в Microsoft Office, основных сборок взаимодействия (PIA) возвращают <xref:System.Object> значения, поскольку они могут возвращать несколько разных типов объектов. Например <xref:Microsoft.Office.Tools.Excel.Workbook.ActiveSheet%2A> возвращает <xref:System.Object> , так как его возвращаемое значение может быть <xref:Microsoft.Office.Interop.Excel.Worksheet> или <xref:Microsoft.Office.Interop.Excel.Chart> объекта, в зависимости от активного листа.  
  
 Если метод или свойство возвращает <xref:System.Object>, необходимо явным образом преобразовать (в Visual Basic) объекта к правильному типу в проектах Visual Basic где **Option Strict** включен. Необходимо явно привести <xref:System.Object> возвращаемых значений в проектах Visual Basic где **Option Strict** отключен.  
  
 В большинстве случаев в справочной документации перечислены возможные типы возвращаемого значения для элемента, который возвращает <xref:System.Object>. Преобразование или приведение объекта дает возможность IntelliSense для объекта в редакторе кода.  
  
 Сведения о преобразовании в Visual Basic см. в разделе [неявные и явные преобразования &#40;Visual Basic&#41; ](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) и [функция CType &#40;Visual Basic&#41;](/dotnet/visual-basic/language-reference/functions/ctype-function).  
  
### <a name="examples"></a>Примеры  
 В следующем примере кода показано, как приведение объекта к определенному типу в проекте Visual Basic где **Option Strict** включен. Такой тип проекта, необходимо явно привести <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> свойства <xref:Microsoft.Office.Interop.Excel.Range>. В этом примере требуется проект Excel на уровне документа с классом листа `Sheet1`.  
  
 [!code-vb[Trin_VstcoreProgramming#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#9)]  
  
 В следующем примере кода демонстрируется неявное приведение объекта к определенному типу в проекте Visual Basic где **Option Strict** выключен или находится в проекте Visual C#, предназначенном [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. В этих типах проектов <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> свойства неявно приведен к <xref:Microsoft.Office.Interop.Excel.Range>. В этом примере требуется проект Excel на уровне документа с классом листа `Sheet1`.  
  
 [!code-vb[Trin_VstcoreProgramming#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#10)]
 [!code-csharp[Trin_VstcoreProgramming#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs#10)]  
  
## <a name="accessing-members-that-are-available-only-through-late-binding"></a>Доступ к членам, которые доступны только через позднее связывание  
 Некоторые свойства и методы в основных сборках взаимодействия Office доступны только с помощью позднего связывания. В проектах Visual Basic where **Option Strict** является или в проектах Visual C#, предназначенных для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], можно использовать компоненты позднего связывания для следующих языков для доступа к членам с поздним связыванием. В проектах Visual Basic where **Option Strict** имеет значение on, необходимо использовать отражение для доступа к этим элементам.  
  
### <a name="examples"></a>Примеры  
 В следующем примере кода показано, как для доступа к членам с поздним связыванием в проекте Visual Basic где **Option Strict** выключен или находится в проекте Visual C#, предназначенном [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. В этом примере обращается к с поздним связыванием **имя** свойство **Открытие файла** диалоговое окно в Word. Чтобы использовать этот пример, запустите его из `ThisDocument` или `ThisAddIn` класса в проекте Word.  
  
 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]  
  
 В следующем примере кода показано, как использовать отражение для выполнения той же задачи в проекте Visual Basic где **Option Strict** включен.  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]  
  
## <a name="see-also"></a>См. также  
 [Написание кода в решениях Office](../vsto/writing-code-in-office-solutions.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Использование типа dynamic &#40;C&#35; руководство по программированию&#41;](/dotnet/csharp/programming-guide/types/using-type-dynamic)   
 [Оператор Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Reflection (C#)](/dotnet/csharp/programming-guide/concepts/reflection) (Отражение (C#))  
 [Reflection (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection) (Отражение (Visual Basic))  
 [Проектирование и создание решений Office](../vsto/designing-and-creating-office-solutions.md)  
  
  