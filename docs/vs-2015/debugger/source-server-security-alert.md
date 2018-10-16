---
title: Источник предупреждения безопасности сервера | Документация Майкрософт
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
- vs.debug.sourceserver.enablewarning
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 8451c281-6914-469c-b80c-6271cc3f3d17
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8f75ae71cb03e4811e5fa0599bd1ee51371c7891
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49230105"
---
# <a name="source-server-security-alert"></a>Предупреждения безопасности сервера системы управления версиями
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При использовании сервера системы управления версиями применяйте только файлы символов из известного надежного места расположения.  
  
 Это предупреждение появляется при включенной поддержке сервера системы управления версиями. Команды сервера системы управления версиями внедрены в файлы символов отладки (PDB-файлы). Убедитесь, что известно, откуда появились данные PDB-файлы.  
  
> [!IMPORTANT]
>  Следует принимать во внимание следующие потенциальные угрозы безопасности при использовании сервера системы управления версиями: в PDB-файл приложения могут быть внедрены произвольные команды, так что следует убедиться, что в файле srcsrv.ini перечислены только те команды, которые надо выполнить. Любая попытка выполнить команду не из файла srcsvr.ini вызовет диалоговое окно подтверждения. Дополнительные сведения см. в разделе [предупреждение системы безопасности: отладчик должен выполнить ненадежную команду](../debugger/security-warning-debugger-must-execute-untrusted-command.md). Параметры команд не проверяются, поэтому будьте внимательны с доверенными командами. Например, при доверии команде сmd.exe пользователь-злоумышленник может указать параметры, которые сделают команду опасной.  
  
## <a name="see-also"></a>См. также  
 [Указание файлов символов (.pdb) и исходных файлов](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Безопасность отладчика](../debugger/debugger-security.md)   
 [Исходный сервер](http://msdn.microsoft.com/library/windows/desktop/ms680641.aspx)



