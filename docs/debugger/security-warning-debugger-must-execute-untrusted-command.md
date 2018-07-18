---
title: 'Предупреждение системы безопасности: Отладчик должен выполнить ненадежную команду | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 77554795772a5a9e2ce5d9bbe9f620923bc20184
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
ms.locfileid: "31479933"
---
# <a name="security-warning-debugger-must-execute-untrusted-command"></a>Security Warning: Debugger Must Execute Untrusted Command
Это диалоговое окно с предупреждением появляется при использовании сервера системы управления версиями. Оно указывает, что команды, которую должен выполнить отладчик для получения исходного кода, нет в списке доверенных команд для сервера системы управления версиями, содержащемся в файле srcsvr.ini. Если это допустимая команда, ее можно добавить в файл srcsvr.ini. В противном случае ее не следует выполнять. Дополнительные сведения см. в разделе [Указание файлов символов (.pdb) и файлов с исходным кодом](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
## <a name="message-text"></a>Текст сообщения  
 **Отладчик должен выполнить следующую команду без доверия, чтобы получить исходный код с исходного сервера.**  
  
 **Если файл символов отладки (\*PDB-файл) — не из известного и надежного источника, эта команда может быть недопустимой или опасной.**  
  
 **Вы действительно хотите выполнить эту команду?**  
  
## <a name="uielement-list"></a>Список элементов пользовательского интерфейса  
 Текстовое поле  
 Команда из PDB-файла, подлежащая выполнению.  
  
 Запуск  
 Позволить выполнить команду.  
  
 Не выполнять  
 Прекратить выполнение команды и загрузку файла с сервера системы управления версиями.  
  
## <a name="see-also"></a>См. также  
 [Укажите символов (.pdb) и исходных файлов](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Безопасность отладчика](../debugger/debugger-security.md)   
 [Исходный сервер](http://msdn.microsoft.com/library/windows/desktop/ms680641\(v=vs.85\).aspx)