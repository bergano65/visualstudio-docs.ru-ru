---
title: Пример файла Dia2dump | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- sample applications [DIA SDK]
- Dia2dump sample [DIA SDK]
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a817720c1ad73b666e0c9a586bb583120a2533c1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68197599"
---
# <a name="dia2dump-sample"></a>Пример файла Dia2dump
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Пример файла Dia2dump устанавливается вместе с Visual Studio и содержит исходного кода dia2dump.cpp. Скомпилированный исполняемый файл запускается из командной строки и отображает содержимое весь файл базы данных программы (PDB-файл).  
  
### <a name="to-install-the-sample"></a>Чтобы установить пример  
  
1. Убедитесь, что компьютер отвечает всем требованиям установки, описанные в начальной странице установки Visual Studio.  
  
2. Установите Visual Studio и выполните все инструкции установки и настройки для включенные примеры.  
  
#### <a name="to-build-the-sample"></a>Сборка образца  
  
1. Откройте файл Dia2dump.sln в Visual Studio. (При необходимости, Visual Studio сначала поможет вам обновить проект файла Dia2dump.)  
  
2. На страницах свойств проекта в **C/C++** &#124; **Общие** &#124; **Дополнительные каталоги включаемых файлов** свойство, укажите `..\DIA SDK\include` каталога. Это гарантирует, что компилятор может найти файл dia2.h.  
  
3. В меню **Построить** выберите пункт **Перестроить решение**.  
  
4. Закройте Visual Studio.  
  
#### <a name="to-run-the-sample"></a>Выполнение образца  
  
1. Откройте командную строку и введите следующую команду:  
  
    ```  
    dia2dump filename  
    ```  
  
## <a name="see-also"></a>См. также  
 [Исходного кода Dia2dump.cpp](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)   
 [Практическое руководство. Устранение неполадок, связанных с неудачными обновлениями проектов Visual Studio](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md)
