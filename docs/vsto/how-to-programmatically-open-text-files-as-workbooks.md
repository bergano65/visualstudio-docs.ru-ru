---
title: "Как: открытие текстовых файлов как книг | Документы Microsoft"
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
- workbooks, opening text files as
- text [Office development in Visual Studio], text files
- text files, opening as workbooks
ms.assetid: 056ae3d0-7fe7-4c28-a2a5-5a948baee0e6
caps.latest.revision: "47"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: dbd39969fba90613594bbbc0b2ea4d2c12825af7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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
  
  