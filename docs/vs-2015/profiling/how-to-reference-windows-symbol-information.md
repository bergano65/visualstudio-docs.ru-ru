---
title: Практическое руководство. Справочная информация о символах Windows | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance tools, symbol servers
- servers, symbol servers
- profiling tools, symbol servers
- symbol servers
ms.assetid: b7c67318-6be2-4b1e-a161-077b1f4a7c30
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 385b9e4511c44c02a358eb88471cd8369971ed1c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572675"
---
# <a name="how-to-reference-windows-symbol-information"></a>Практическое руководство. Справочная информация о символах Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: справочная информация о символах Windows](https://docs.microsoft.com/visualstudio/profiling/how-to-reference-windows-symbol-information).  
  
Файлы символов (PDB) средств профилирования Visual Studio используются для разрешения символьных имен, например имен функций в двоичных файлах программ. Вы можете выполнить следующие действия, чтобы автоматически скачать и изменить правильные PDB-файлы для версии Windows на локальном компьютере.  
  
> [!NOTE]
>  Этот параметр не влияет на существующие отчеты. Только отчеты, созданные после указания сервера символов, будут включать сведения о символах.  
  
 Дополнительные сведения см. в разделе [Указание файлов символов (.pdb) и файлов с исходным кодом](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
### <a name="to-use-the-microsoft-symbol-server"></a>Использование сервера символов Майкрософт  
  
1.  Создайте папку для хранения файла сведений о символах, например C:\SymbolCache.  
  
2.  В меню **Сервис** выберите пункт **Параметры**.  
  
     Откроется диалоговое окно **Параметры** .  
  
3.  Разверните дерево **Отладка**, а затем щелкните **Символы**.  
  
4.  В поле **Места размещения файлов символов (.pdb)** выберите **Серверы символов Майкрософт**.  
  
5.  В поле **Кэшировать символы с серверов символов в следующий каталог** введите путь к папке, которая была создана на шаге 1, например:  
  
     **C:\SymbolCache**  
  
     Можно также нажать кнопку с многоточием (**...** ) и выбрать каталог в диалоговом окне **Выбрать папку**.  
  
## <a name="see-also"></a>См. также  
 [Настройка сеансов анализа производительности](../profiling/configuring-performance-sessions.md)   
 [Практическое руководство. Сериализация сведений о символах](../profiling/how-to-serialize-symbol-information.md)



