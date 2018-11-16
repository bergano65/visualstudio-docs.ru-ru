---
title: Практическое руководство. Справочная информация о символах Windows | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
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
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c18825a27bfefdd1a6c817951983d85ac459b78b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51763592"
---
# <a name="how-to-reference-windows-symbol-information"></a>Практическое руководство. Справочная информация о символах Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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



