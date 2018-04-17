---
title: Предупреждения безопасности сервера источника | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4ef0d4a7569913caf31ad94c3651173e9b30156a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="source-server-security-alert"></a>Предупреждения безопасности сервера системы управления версиями
При использовании сервера системы управления версиями применяйте только файлы символов из известного надежного места расположения.  
  
 Это предупреждение появляется при включенной поддержке сервера системы управления версиями. Команды сервера системы управления версиями внедрены в файлы отладочных символов (***.pdb** файлов). Убедитесь, что известно, откуда появились данные PDB-файлы.  
  
> [!IMPORTANT]
>  Следует принимать во внимание следующие потенциальные угрозы безопасности при использовании сервера системы управления версиями: в PDB-файл приложения могут быть внедрены произвольные команды, так что следует убедиться, что в файле srcsrv.ini перечислены только те команды, которые надо выполнить. Любая попытка выполнить команду не из файла srcsvr.ini вызовет диалоговое окно подтверждения. Для получения дополнительной информации см. [Security Warning: Debugger Must Execute Untrusted Command](../debugger/security-warning-debugger-must-execute-untrusted-command.md). Параметры команд не проверяются, поэтому будьте внимательны с доверенными командами. Например, при доверии команде сmd.exe пользователь-злоумышленник может указать параметры, которые сделают команду опасной.  
  
## <a name="see-also"></a>См. также  
 [Укажите символов (.pdb) и исходных файлов](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Безопасность отладчика](../debugger/debugger-security.md)   
 [Исходный сервер](http://msdn.microsoft.com/library/windows/desktop/ms680641.aspx)
