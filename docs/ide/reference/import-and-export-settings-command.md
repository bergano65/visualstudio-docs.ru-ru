---
title: "Импорт и экспорт параметров — команда | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
caps.latest.revision: 5
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: dca11a81e650f0470c891cb79623f9cc088ea669
ms.contentlocale: ru-ru
ms.lasthandoff: 05/24/2017

---
# <a name="import-and-export-settings-command"></a>Импорт и экспорт параметров - команда
Импортирует, экспортирует или сбрасывает параметры [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]  
```  
  
## <a name="switches"></a>Переключатели  
 /export:`filename`  
 Необязательно. Экспортирует текущие параметры в указанный файл  
  
 /import:`filename`  
 Необязательно. Импортирует текущие параметры в указанный файл  
  
 /reset  
 Необязательно. Сбрасывает текущие параметры  
  
## <a name="remarks"></a>Примечания  
 Выполнение этой команды без параметров командной строки открывает мастер **Импорт и экспорт параметров**. Дополнительные сведения см. в статье [Практическое руководство. Совместное использование параметров на разных компьютерах или в разных версиях Visual Studio](http://msdn.microsoft.com/en-us/1131fb10-35c1-42da-9cd8-91aa3235b882).  
  
## <a name="example"></a>Пример  
 Следующая команда экспортирует текущие параметры в файл `MyFile.vssettings`.  
  
```  
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"  
```  
  
## <a name="see-also"></a>См. также  
 [Персонализация интегрированной среды разработки Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)   
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)
