---
title: 'Практическое: программное открытие текстовых файлов как книг Excel'
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
ms.openlocfilehash: b7bc7caa5dbceb727394b8543b7659cc43e64a36
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257651"
---
# <a name="how-to-programmatically-open-text-files-as-workbooks"></a>Практическое: программное открытие текстовых файлов как книг Excel
  Текстовый файл можно открыть как книгу. Необходимо передать имя текстовый файл, который требуется открыть. Можно указать несколько необязательных параметров, например, номер строки для синтаксического анализа и формат столбцов данных в файле.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="example"></a>Пример  
 [!code-csharp[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#80)]
 [!code-vb[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#80)]  
  
## <a name="compile-the-code"></a>Компиляция кода  
 В этом примере требуются следующие компоненты:  
  
-   Файл с разделителями-запятыми, с именем `Test.txt` , содержащий по крайней мере три строки текста.  
  
-   Текстовый файл `Test.txt` сохраняются на диске C.  
  
## <a name="see-also"></a>См. также  
 [Работа с книгами](../vsto/working-with-workbooks.md)   
 [Практическое: программное открытие книг Excel](../vsto/how-to-programmatically-open-workbooks.md)   
 [Практическое: программное создание книг Excel](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [Практическое: программное Сохранение книг Excel](../vsto/how-to-programmatically-save-workbooks.md)   
 [Практическое: программное закрытие книг Excel](../vsto/how-to-programmatically-close-workbooks.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  