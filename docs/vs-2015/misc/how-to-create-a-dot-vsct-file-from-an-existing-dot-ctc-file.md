---
title: Практическое руководство. Создать. Vsct-файл из существующего. Файла ctc | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating based on a .ctc file
ms.assetid: 700e80a4-c1e1-4178-af53-45e86dd2c08b
caps.latest.revision: 9
manager: jillfra
ms.openlocfilehash: 2d5ba5a271cd7132d9750fc0569b801022aeb932
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60117860"
---
# <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Практическое руководство. Создать. Vsct-файл из существующего. Файла ctc
Вы можете создать файл VSTC на основе XML из существующего исходного CTC-файла таблицы команд. Таким образом можно воспользоваться новым форматом компилятора таблицы команд [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] на основе XML (VSCT).  
  
### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>Создание файла VSCT на основе файла CTC  
  
1. Получите копию языка Perl.  
  
2. Получите копию скрипта ConvertCTCToVSCT.pl, Perl, обычно находится в  *\<путь установки пакета SDK для Visual Studio >* \VisualStudioIntegration\Tools\bin папку.  
  
3. Получите копию исходного файла CTC, который нужно преобразовать.  
  
4. Поместите файлы в один каталог.  
  
5. В окне командной строки [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] перейдите в этот каталог.  
  
6. Тип  
  
    ```  
    perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct  
    ```  
  
     Здесь PkgCmd.ctc — это имя файла CTC, а PkgCmd.vsct — имя файла VSCT, который нужно создать.  
  
     Будет создан исходный VSCT-файл таблицы команд XML. Этот файл можно скомпилировать с помощью Vsct.exe, компилятора VSCT, как и любой другой файл VSCT.  
  
    > [!NOTE]
    >  Чтобы повысить удобочитаемость файла VSCT, можно переформатировать комментарии XML.  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Создать. Файл Vsct](../extensibility/internals/how-to-create-a-dot-vsct-file.md)   
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)