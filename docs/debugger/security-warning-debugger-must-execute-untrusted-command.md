---
title: Предупреждение системы безопасности. Отладчик должен выполнить ненадежную команду | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.securityalert
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: e5c004b3-b364-4098-ac98-770076ca9981
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3e421521bd40ff4369433b0a0c3c323579e36125
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53855619"
---
# <a name="security-warning-debugger-must-execute-untrusted-command"></a>Предупреждение системы безопасности. Отладчик должен выполнить команду без доверия
Это диалоговое окно с предупреждением появляется при использовании сервера системы управления версиями. Оно указывает, что команды, которую должен выполнить отладчик для получения исходного кода, нет в списке доверенных команд для сервера системы управления версиями, содержащемся в файле srcsvr.ini. Если это допустимая команда, ее можно добавить в файл srcsvr.ini. В противном случае ее не следует выполнять. Дополнительные сведения см. в разделе [Указание файлов символов (.pdb) и файлов с исходным кодом](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
## <a name="message-text"></a>Текст сообщения  
 **Отладчик должен выполнить эту команду, для которой не установлено доверие, чтобы получить исходный код с сервера системы управления версиями.**  
  
 **Если файл отладочных символов (\*.pdb) получен из ненадежного источника, эта команда может быть недопустимой или опасной.**  
  
 **Вы хотите выполнить эту команду?**  
  
## <a name="uielement-list"></a>Список элементов пользовательского интерфейса  
 Текстовое поле  
 Команда из PDB-файла, подлежащая выполнению.  
  
 Выполнить  
 Позволить выполнить команду.  
  
 Не выполнять  
 Прекратить выполнение команды и загрузку файла с сервера системы управления версиями.  
  
## <a name="see-also"></a>См. также раздел  
 [Указание файлов символов (PDB) и файлов с исходным кодом](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Безопасность отладчика](../debugger/debugger-security.md)   
 [Исходный сервер](/windows/desktop/Debug/source-server-and-source-indexing)