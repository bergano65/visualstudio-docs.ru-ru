---
title: Предупреждения безопасности сервера системы управления версиями | Документация Майкрософт
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
ms.openlocfilehash: 3f8b122deab5dbdc30b129bce221a804f8c53aa3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65699326"
---
# <a name="source-server-security-alert"></a>Предупреждения безопасности сервера системы управления версиями
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При использовании сервера системы управления версиями применяйте только файлы символов из известного надежного места расположения.  
  
 Это предупреждение появляется при включенной поддержке сервера системы управления версиями. Команды сервера системы управления версиями внедрены в файлы символов отладки (PDB-файлы). Убедитесь, что известно, откуда появились данные PDB-файлы.  
  
> [!IMPORTANT]
> При использовании исходного сервера необходимо принимать во внимание следующие потенциальные угрозы безопасности. В PDB-файл приложения можно внедрять произвольные команды, поэтому убедитесь, что в него помещены только те, которые требуется выполнить в файле srcsrv.ini. Любая попытка выполнить команду не из файла srcsvr.ini вызовет диалоговое окно подтверждения. Дополнительные сведения см. в разделе [предупреждение системы безопасности: отладчик должен выполнить команду](../debugger/security-warning-debugger-must-execute-untrusted-command.md), не являющейся доверенной. Для параметров команды проверка не выполняется, поэтому будьте внимательны при использовании доверенных команд. Например, при доверии команде сmd.exe пользователь-злоумышленник может указать параметры, которые сделают команду опасной.  
  
## <a name="see-also"></a>См. также:  
 [Указание символов (. pdb) и исходных файлов](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Безопасность отладчика](../debugger/debugger-security.md)   
 [Исходный сервер](https://msdn.microsoft.com/library/windows/desktop/ms680641.aspx)
