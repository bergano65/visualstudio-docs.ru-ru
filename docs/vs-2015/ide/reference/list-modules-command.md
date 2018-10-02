---
title: Команда List Modules | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- debug.listmodules
helpviewer_keywords:
- Debug.ListModules command
- ListModules command
- list modules command
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1593879f59642347f58d9c8229aac7d2a9d70261
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572676"
---
# <a name="list-modules-command"></a>Команда List Modules
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [команда List Modules](https://docs.microsoft.com/visualstudio/ide/reference/list-modules-command).  
  
  
Отображает список модулей для текущего процесса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]  
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]  
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]  
```  
  
#### <a name="parameters"></a>Параметры  
 /Address:`yes|no`  
 Необязательный. Указывает, нужно ли отображать адреса модулей в памяти. Значение по умолчанию — `yes`.  
  
 /Name:`yes|no`  
 Необязательный. Указывает, нужно ли отображать имена модулей. Значение по умолчанию — `yes`.  
  
 /Order:`yes|no`  
 Необязательный. Указывает, нужно ли отображать порядок модулей. Значение по умолчанию — `no`.  
  
 /Path:`yes|no`  
 Необязательный. Указывает, нужно ли отображать пути к модулям. Значение по умолчанию — `yes`.  
  
 /Process:`yes|no`  
 Необязательный. Указывает, нужно ли отображать процессы модулей. Значение по умолчанию — `no`.  
  
 /SymbolFile:`yes|no`  
 Необязательный. Указывает, нужно ли отображать файлы символов модулей. Значение по умолчанию — `no`.  
  
 /SymbolStatus:`yes|no`  
 Необязательный. Указывает, нужно ли отображать состояния символов модулей. Значение по умолчанию — `yes`.  
  
 /Timestamp:`yes|no`  
 Необязательный. Указывает, нужно ли отображать метки времени модулей. Значение по умолчанию — `no`.  
  
 /Version:`yes|no`  
 Необязательный. Указывает, нужно ли отображать версии модулей. Значение по умолчанию — `no`.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="example"></a>Пример  
 В этом примере демонстрируется создание списка имен модулей для текущего процесса с указанием адресов и меток времени.  
  
```  
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no  
```  
  
## <a name="see-also"></a>См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Практическое руководство. Использование окна модулей](../../debugger/how-to-use-the-modules-window.md)



