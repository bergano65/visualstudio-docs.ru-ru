---
title: "-ResetAddin (devenv.exe) | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- disable addin
- addin state
- reset addin
ms.assetid: 9e339c8d-d768-4d86-8f45-2f479fc8255b
caps.latest.revision: 5
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: cfc96ba712fbc057f9e6e57c61c80ebe38bd662c
ms.lasthandoff: 02/22/2017

---
# <a name="resetaddin-devenvexe"></a>/ResetAddin (devenv.exe)
Удаляет команды и интерфейс пользователя команд, связанный с указанной надстройкой.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Devenv /ResetAddin AddIn  
```  
  
## <a name="arguments"></a>Аргументы  
 `AddIn`  
 Необязательно. Имя команды надстройки.  
  
## <a name="remarks"></a>Примечания  
 По умолчанию имя команды надстройки — *\<AddInSolutionName>*.Connect*.\<AddInSolutionName>*. Оно отображается в файле Connect.cs как параметр `commandName` метода `Exec`. Имя команды также можно проверить, начав вводить имя надстройки в окне "Команды" Visual Studio. Функция Intellisense закончит ввод.  
  
## <a name="example"></a>Пример  
 Следующий пример запускает Visual Studio и предотвращает запуск надстройки `MyAddin` при загрузке.  
  
```  
Devenv.exe /ResetAddin MyAddin.Connect.MyAddin  
```  
  
## <a name="see-also"></a>См. также  
 [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)
