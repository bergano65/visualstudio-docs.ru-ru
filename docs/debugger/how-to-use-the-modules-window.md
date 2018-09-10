---
title: Просматривать библиотеки DLL и исполняемых файлов в отладчике | Документация Майкрософт
ms.custom: H1Hack27Feb2017
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.modules
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, Modules window
- Modules window
- executable files, displaying while debugging
- debugging [Visual Studio], displaying modules
- DLLs, displaying while debugging
- modules, displaying
ms.assetid: d840fdca-b035-4452-b652-72580c831896
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f582c435239c83503b179d6bb5e142936a41cb4b
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279015"
---
# <a name="view-dlls-and-executables-using-the-modules-window-in-the-visual-studio-debugger"></a>Просмотр библиотек DLL и исполняемые файлы, с помощью окна "Модули" в отладчике Visual Studio
 
**Модули** окне выводится список библиотек DLL и исполняемые файлы (EXE), которые используются приложением и отображает соответствующую информацию для каждого. 

> [!NOTE]
>  Эта возможность недоступна при отладке SQL и скриптов. 
  
### <a name="to-display-the-modules-window"></a>Для отображения окна "Модули"  
  
-   При отладке, выберите **Отладка > Windows** и нажмите кнопку **модули**.  
  
     По умолчанию **модули** окна модули упорядочены в порядке загрузки. При этом можно выбрать сортировку по любому столбцу.  
  
### <a name="to-sort-by-any-column"></a>Выбор сортировки по произвольному столбцу  
  
-   Нажмите кнопку вверху столбца.  
  
     Можно загрузить символы или указать путь к символам из **модули** окна с помощью контекстного меню.  
  
## <a name="loading-symbols"></a>Загрузка символов  
 В **модули** окно, можно видеть, какие модули загружены символы отладки. Эта информация отображается в **состояние символов** столбца. Если указано состояние **loadingCannot пропущено найти или открыть PDB-файл**, или **загрузка отключена параметром включения/исключения**, можно настроить отладчик на загрузку символов с общедоступных символов Майкрософт серверы или загрузить символы из каталога символов на компьютере. Дополнительные сведения см. в разделе [Указание файлов символов (.pdb) и исходных файлов](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### <a name="to-load-symbols-manually"></a>Загрузка символов вручную  
  
1.  В **модули** окно, щелкните правой кнопкой мыши, либо модуль, для которого не загружены символы.  
  
2.  Пункты **загрузить символы из** и нажмите кнопку **серверы символов Microsoft** или **путь к символам**.  
  
#### <a name="to-change-symbol-load-settings"></a>Изменение параметров загрузки символов  
  
1.  В **модули** окно, щелкните правой кнопкой мыши любой модуль.  
  
2.  Нажмите кнопку **параметры символов**.  
  
     Теперь можно изменить параметры загрузки символов, как описано в разделе [определение расположения символов и поведения при загрузке](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior). Изменения вступают в силу только после перезапуска сеанса отладки.  
  
#### <a name="to-change-symbol-load-behavior-for-a-specific-module"></a>Изменение поведения загрузки символов для конкретного модуля  
  
1.  В **модули** окно, щелкните правой кнопкой мыши модуль.  
  
2.  Пункты **параметры автоматической загрузки символов** и нажмите кнопку **всегда загружать вручную** или **по умолчанию**. Изменения вступают в силу только после перезапуска сеанса отладки.  
  
## <a name="see-also"></a>См. также  
 [Прерывание выполнения](/previous-versions/visualstudio/visual-studio-2010/7z9se2d8(v=vs.100))   
 [Просмотр данных в отладчике](../debugger/viewing-data-in-the-debugger.md)   
 [Указание файлов символов (.pdb) и файлов с исходным кодом](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)