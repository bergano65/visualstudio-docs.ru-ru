---
title: Оповещение системы безопасности исходного сервера | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.enablewarning
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 8451c281-6914-469c-b80c-6271cc3f3d17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 69511c2f83570abf37ef4bea8b71c8f59431a128
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72729563"
---
# <a name="source-server-security-alert"></a>Предупреждения безопасности сервера системы управления версиями
При использовании сервера системы управления версиями применяйте только файлы символов из известного надежного места расположения.

 Это предупреждение появляется при включенной поддержке сервера системы управления версиями. Команды сервера системы управления версиями внедрены в файлы отладочных символов ( **\*PDB**-файлы). Убедитесь, что известно, откуда появились данные PDB-файлы.

> [!IMPORTANT]
> Следует принимать во внимание следующие потенциальные угрозы безопасности при использовании сервера системы управления версиями: в PDB-файл приложения могут быть внедрены произвольные команды, так что следует убедиться, что в файле srcsrv.ini перечислены только те команды, которые надо выполнить. Любая попытка выполнить команду не из файла srcsvr.ini вызовет диалоговое окно подтверждения. Для получения дополнительной информации см. [Security Warning: Debugger Must Execute Untrusted Command](../debugger/security-warning-debugger-must-execute-untrusted-command.md). Параметры команд не проверяются, поэтому будьте внимательны с доверенными командами. Например, при доверии команде сmd.exe пользователь-злоумышленник может указать параметры, которые сделают команду опасной.

## <a name="see-also"></a>См. также
- [Указание файлов символов (.pdb) и файлов с исходным кодом](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Безопасность отладчика](../debugger/debugger-security.md)
- [Исходный сервер](/windows/desktop/Debug/source-server-and-source-indexing)
