---
title: Создание переносимых файлов данных профилирования в командной строке | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 314dc97e5881949ee69131576932db1865969b2c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573407"
---
# <a name="creating-portable-profiling-data-files-from-the-command-line"></a>Создание переносимых файлов данных профилирования в командной строке
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Создание переносимых файлов с данными профилирования из командной строки](https://docs.microsoft.com/visualstudio/profiling/creating-portable-profiling-data-files-from-the-command-line).  
  
Чтобы упростить общий доступ к данным профилирования, вы можете использовать программу командной строки [VSPerfReport](../profiling/vsperfreport.md) в целях внедрения символов для сеанса профилирования в VSP-файл.  
  
 Вы также можете создать файл предварительно проанализированных данных профилирования (VSPS), который меньше по размеру и быстрее загружается в интегрированной среде разработки.  
  
> [!NOTE]
>  Убедитесь, что файлы символов (PDB) доступны для **VSPerfReport**. Дополнительные сведения см. в статье [Практическое руководство. Определение расположения файлов символов с помощью командной строки](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).  
>   
>  Дополнительные сведения о пути к **VSReport** см. в статье [Указание пути к средствам командной строки](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
>  Данные профилирования в VSPS-файле невозможно отфильтровать.  
  
### <a name="to-embed-the-symbols-for-a-profiling-run-into-a-profiling-data-vsp-file"></a>Внедрение символов для сеанса профилирования в файл данных профилирования (VSP)  
  
-   В окне командной строки введите следующую команду:  
  
     \<Путь>**VSPerfReport \<** VSP-файл> **/PackSymbols**  
  
     По умолчанию VSPS-файл имеет базовое имя VSP-файла. Вы можете указать альтернативное имя с помощью параметра **Вывод**.  
  
### <a name="to-create-a-summary-profiling-data-file"></a>Создание сводного файла данных профилирования  
  
-   В окне командной строки введите следующую команду:  
  
     \<Путь>**VSPerfReport \<** VSP-файл> **/SummaryFile** [**/Output:**\<имя файла>]  
  
     По умолчанию VSPS-файл имеет базовое имя VSP-файла. Вы можете указать альтернативное имя с помощью параметра **Вывод**.



