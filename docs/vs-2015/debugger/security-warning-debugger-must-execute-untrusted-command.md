---
title: Предупреждение системы безопасности. Отладчик должен выполнить команду без доверия | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.securityalert
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: e5c004b3-b364-4098-ac98-770076ca9981
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2a29ba026f9b3c2b8839d474c2d0833eb79f7ffd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683300"
---
# <a name="security-warning-debugger-must-execute-untrusted-command"></a>Предупреждение системы безопасности. Отладчик должен выполнить команду без доверия
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
## <a name="see-also"></a>См. также:  
 [Указание символов (. pdb) и исходных файлов](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Безопасность отладчика](../debugger/debugger-security.md)   
 [Исходный сервер](https://msdn.microsoft.com/library/windows/desktop/ms680641\(v=vs.85\).aspx)
