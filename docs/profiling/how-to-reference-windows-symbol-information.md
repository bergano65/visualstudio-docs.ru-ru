---
title: Как выполнить Справочная информация о символах Windows | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, symbol servers
- servers, symbol servers
- profiling tools, symbol servers
- symbol servers
ms.assetid: b7c67318-6be2-4b1e-a161-077b1f4a7c30
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 347b35a1ed47236c0d6e6c187224ee50fd79852c
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56619892"
---
# <a name="how-to-reference-windows-symbol-information"></a>Как выполнить Справочная информация о символах Windows
Файлы символов (*PDB*) средств профилирования Visual Studio используются для разрешения символьных имен, например имен функций в двоичных файлах программ. Вы можете выполнить следующие действия, чтобы автоматически скачать и изменить правильные *PDB*-файлы для версии Windows на локальном компьютере.

> [!NOTE]
>  Этот параметр не влияет на существующие отчеты. Только отчеты, созданные после указания сервера символов, будут включать сведения о символах.

 Дополнительные сведения см. в разделе [Указание файлов символов (*PDB*) и исходных файлов](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

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
- [Настройка сеансов анализа производительности](../profiling/configuring-performance-sessions.md)
- [Практическое руководство. Сериализация сведений о символах](../profiling/how-to-serialize-symbol-information.md)