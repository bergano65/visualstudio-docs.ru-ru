---
title: 'Как: открытие текстовых файлов как книг | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening text files as
- text [Office development in Visual Studio], text files
- text files, opening as workbooks
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cafe64ce693972bd9c254a6bdfc1dcbf70f004c9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-open-text-files-as-workbooks"></a>Практическое руководство. Программное открытие текстовых файлов как книг Excel
  Можно открыть текстовый файл как книгу. Необходимо передать имя текстового файла, который вы хотите открыть. Можно указать несколько необязательных параметров, например, номер первой строки для синтаксического анализа и формат столбцов данных в файле.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="example"></a>Пример  
 [!code-csharp[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#80)]
 [!code-vb[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#80)]  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Для этого примера требуются следующие компоненты:  
  
-   Файл с разделителями-запятыми, с именем `Test.txt` , содержащий по крайней мере три строки текста.  
  
-   Текстовый файл `Test.txt` сохранялись на диске C.  
  
## <a name="see-also"></a>См. также  
 [Работа с книгами](../vsto/working-with-workbooks.md)   
 [Как: открытие книг](../vsto/how-to-programmatically-open-workbooks.md)   
 [Как: программным путем создания новых книг](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [Как: программное Сохранение книг](../vsto/how-to-programmatically-save-workbooks.md)   
 [Как: программное закрытие книг Excel](../vsto/how-to-programmatically-close-workbooks.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  