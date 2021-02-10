---
title: Справочная информация о символах Windows | Документация Майкрософт
description: Сведения о файлах символов (PDB) средств профилирования Visual Studio, которые используются для разрешения символьных имен, например имен функций в двоичных файлах программ.
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- performance tools, symbol servers
- servers, symbol servers
- profiling tools, symbol servers
- symbol servers
ms.assetid: b7c67318-6be2-4b1e-a161-077b1f4a7c30
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c788be648b77a36b8da7027c89a7d9cb047b57d5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907099"
---
# <a name="how-to-reference-windows-symbol-information"></a>Практическое руководство. Справочная информация о символах Windows
Файлы символов (*PDB*) средств профилирования Visual Studio используются для разрешения символьных имен, например имен функций в двоичных файлах программ. Вы можете выполнить следующие действия, чтобы автоматически скачать и изменить правильные *PDB*-файлы для версии Windows на локальном компьютере.

> [!NOTE]
> Этот параметр не влияет на существующие отчеты. Только отчеты, созданные после указания сервера символов, будут включать сведения о символах.

 Дополнительные сведения см. в разделе [Указание файлов символов (*PDB*) и исходных файлов](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

### <a name="to-use-the-microsoft-symbol-server"></a>Использование сервера символов Майкрософт

1. Создайте папку для хранения файла сведений о символах, например C:\SymbolCache.

2. В меню **Сервис** выберите пункт **Параметры**.

     Откроется диалоговое окно **Параметры** .

3. Разверните дерево **Отладка**, а затем щелкните **Символы**.

4. В поле **Места размещения файлов символов (.pdb)** выберите **Серверы символов Майкрософт**.

5. В поле **Кэшировать символы с серверов символов в следующий каталог** введите путь к папке, которая была создана на шаге 1, например:

     **C:\SymbolCache**

     Можно также нажать кнопку с многоточием ( **...** ) и выбрать каталог в диалоговом окне **Выбрать папку**.

## <a name="see-also"></a>См. также
- [Настройка сеансов анализа производительности](../profiling/configuring-performance-sessions.md)
- [Практическое руководство. Сериализация сведений о символах](../profiling/how-to-serialize-symbol-information.md)
