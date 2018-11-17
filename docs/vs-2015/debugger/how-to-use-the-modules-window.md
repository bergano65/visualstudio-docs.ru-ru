---
title: 'Практическое: использование окна "Модули" | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.modules
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Modules window
- Modules window
- executable files, displaying while debugging
- debugging [Visual Studio], displaying modules
- DLLs, displaying while debugging
- modules, displaying
ms.assetid: d840fdca-b035-4452-b652-72580c831896
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fea513b7593e260b5f5fb71e40ced98a1f8cc279
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764404"
---
# <a name="how-to-use-the-modules-window"></a>Практическое руководство. Использование окна модулей
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ПРИМЕЧАНИЕ.]
>  Эта возможность недоступна при отладке SQL и скриптов.  
  
 **Модули** окне перечислены библиотеки DLL и EXE-файла, которые используются приложением и отображает соответствующую информацию для каждого.  
  
### <a name="to-display-the-modules-window-in-break-mode-or-in-run-mode"></a>Вывод окна "Модули" в режиме приостановки или выполнения  
  
-   На **Отладка** меню, выберите **Windows**, а затем нажмите кнопку **модули**.  
  
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
 [Прерывание выполнения](http://msdn.microsoft.com/en-us/30fc4643-f337-4651-b1ff-f2de2c098d40)   
 [Просмотр данных в отладчике](../debugger/viewing-data-in-the-debugger.md)   
 [Указание файлов символов (.pdb) и файлов с исходным кодом](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)





