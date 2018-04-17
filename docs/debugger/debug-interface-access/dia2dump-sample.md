---
title: Пример файла Dia2dump | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sample applications [DIA SDK]
- Dia2dump sample [DIA SDK]
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: acec3fa2def0c478c9d94d71a80b89cda6709897
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="dia2dump-sample"></a>Пример файла Dia2dump
Пример файла Dia2dump устанавливается вместе с Visual Studio и содержит исходного кода dia2dump.cpp. Исполняемый файл запускается из командной строки и отображает содержимое PDB-файла всей программы.  
  
### <a name="to-install-the-sample"></a>Чтобы установить образец  
  
1.  Убедитесь, что системы отвечает всем требованиям установки, описанные в начальной странице установки Visual Studio.  
  
2.  Установите Visual Studio и выполните все настройки и инструкции по установке для включенные примеры.  
  
#### <a name="to-build-the-sample"></a>Сборка образца  
  
1.  Откройте файл Dia2dump.sln в Visual Studio. (При необходимости, Visual Studio сначала поможет вам обновить проект Dia2dump.)  
  
2.  На странице свойств проекта в **C/C++** &#124; **Общие** &#124; **Дополнительные каталоги включаемых файлов** свойство, укажите `..\DIA SDK\include` каталога. Это гарантирует, что компилятор может найти файл dia2.h.  
  
3.  На **построения** меню, нажмите кнопку **Перестроить решение**.  
  
4.  Закройте Visual Studio.  
  
#### <a name="to-run-the-sample"></a>Выполнение образца  
  
1.  Откройте командную строку и введите следующую команду:  
  
    ```  
    dia2dump filename  
    ```  
  
## <a name="see-also"></a>См. также  
 [Исходного кода Dia2dump.cpp](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)   
 [Перенос кода, миграция и обновление проектов Visual Studio](../../porting/port-migrate-and-upgrade-visual-studio-projects.md)