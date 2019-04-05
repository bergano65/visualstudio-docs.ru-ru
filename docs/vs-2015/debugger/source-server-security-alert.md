---
title: Источник предупреждения безопасности сервера | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.enablewarning
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 8451c281-6914-469c-b80c-6271cc3f3d17
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 76d61520bf17ad3230a437c295de387a910f808f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58979284"
---
# <a name="source-server-security-alert"></a>Предупреждения безопасности сервера системы управления версиями
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При использовании сервера системы управления версиями применяйте только файлы символов из известного надежного места расположения.  
  
 Это предупреждение появляется при включенной поддержке сервера системы управления версиями. Команды сервера системы управления версиями внедрены в файлы символов отладки (PDB-файлы). Убедитесь, что известно, откуда появились данные PDB-файлы.  
  
> [!IMPORTANT]
>  Следующие потенциальные угрозы безопасности необходимо принимать во внимание при использовании исходного сервера: Произвольные команды могут быть внедрены в PDB-файл приложения, поэтому убедитесь, что в него помещены только те, которые необходимо выполнить в файле srcsrv.ini. Любая попытка выполнить команду не из файла srcsvr.ini вызовет диалоговое окно подтверждения. Дополнительные сведения см. в разделе [предупреждение системы безопасности: Отладчик должен выполнить ненадежную команду](../debugger/security-warning-debugger-must-execute-untrusted-command.md). Параметры команд не проверяются, поэтому будьте внимательны с доверенными командами. Например, при доверии команде сmd.exe пользователь-злоумышленник может указать параметры, которые сделают команду опасной.  
  
## <a name="see-also"></a>См. также  
 [Указание файлов символов (PDB) и файлов с исходным кодом](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Безопасность отладчика](../debugger/debugger-security.md)   
 [Исходный сервер](http://msdn.microsoft.com/library/windows/desktop/ms680641.aspx)
