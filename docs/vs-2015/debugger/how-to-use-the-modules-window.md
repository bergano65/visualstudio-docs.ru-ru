---
title: Как использовать окно "модули" | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: b592515692e23dce49c125c7895bd158904b653f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696125"
---
# <a name="how-to-use-the-modules-window"></a>Практическое руководство. Использование окна модулей
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ПРИМЕЧАНИЕ
> Эта возможность недоступна при отладке SQL и скриптов.  
  
 В окне **модули** перечислены библиотеки DLL и exe, используемые программой, и отображаются соответствующие сведения для каждого из них.  
  
### <a name="to-display-the-modules-window-in-break-mode-or-in-run-mode"></a>Вывод окна "Модули" в режиме приостановки или выполнения  
  
- В меню **Отладка** выберите пункт **окна**, а затем щелкните **модули**.  
  
     По умолчанию модули в окне **Модули** упорядочены в порядке загрузки. При этом можно выбрать сортировку по любому столбцу.  
  
### <a name="to-sort-by-any-column"></a>Выбор сортировки по произвольному столбцу  
  
- Нажмите кнопку вверху столбца.  
  
     Можно загрузить символы или указать путь к символам из окна " **модули** " с помощью контекстного меню.  
  
## <a name="loading-symbols"></a>Загрузка символов  
 В окне **модули** можно увидеть, в каких модулях загружены отладочные символы. Эти сведения отображаются в столбце **Состояние символов** . Если в поле состояние указано **пропущено лоадингканнот найти или открыть PDB-файл**или **Загрузка отключена с помощью параметра включить/исключить**, отладчик можно будет использовать для загрузки символов с общедоступных серверов символов Майкрософт или для загрузки символов из каталога символов на компьютере. Дополнительные сведения см. в разделе [Указание символов (PDB) и исходных файлов](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) .  
  
#### <a name="to-load-symbols-manually"></a>Загрузка символов вручную  
  
1. В окне **модули** щелкните правой кнопкой мыши модуль, для которого не загружены символы.  
  
2. Укажите пункт **загрузить символы из** , а затем выберите **Серверы символов Майкрософт** или **путь к символам**.  
  
#### <a name="to-change-symbol-load-settings"></a>Изменение параметров загрузки символов  
  
1. В окне **Модули** щелкните правой кнопкой мыши любой модуль.  
  
2. Щелкните **Параметры символов**.  
  
     Теперь можно изменить параметры загрузки символов, как описано в разделе [указание расположений символов и поведение при загрузке](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior). Изменения вступают в силу только после перезапуска сеанса отладки.  
  
#### <a name="to-change-symbol-load-behavior-for-a-specific-module"></a>Изменение поведения загрузки символов для конкретного модуля  
  
1. В окне **Модули** щелкните правой кнопкой мыши требуемый модуль.  
  
2. Укажите **Параметры автоматической загрузки символов** и нажмите кнопку **всегда загружать вручную** или **по умолчанию**. Изменения вступают в силу только после перезапуска сеанса отладки.  
  
## <a name="see-also"></a>См. также:  
 [Прерывание выполнения](https://msdn.microsoft.com/30fc4643-f337-4651-b1ff-f2de2c098d40)   
 [Просмотр данных в отладчике](../debugger/viewing-data-in-the-debugger.md)   
 [Указание файлов символов (.pdb) и файлов с исходным кодом](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
