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
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 36b003f4890b16a7b69f7f66f8b0ef83a0ade7ac
ms.sourcegitcommit: d16c6812b114a8672a58ce78e6988b967498c747
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/02/2018
---
# <a name="resetaddin-devenvexe"></a>/ResetAddin (devenv.exe)
Удаляет команды и интерфейс пользователя команд, связанный с указанной надстройкой.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Devenv /ResetAddin AddIn  
```  
  
## <a name="arguments"></a>Аргументы  
 `AddIn`  
 Необязательный. Имя команды надстройки.  
  
## <a name="remarks"></a>Примечания  
 По умолчанию имя команды надстройки — *\<AddInSolutionName>*.Connect*.\<AddInSolutionName>*. Оно отображается в файле Connect.cs как параметр `commandName` метода `Exec`. Имя команды также можно проверить, начав вводить имя надстройки в окне "Команды" Visual Studio. Функция Intellisense закончит ввод.  
  
## <a name="example"></a>Пример  
 Следующий пример запускает Visual Studio и предотвращает запуск надстройки `MyAddin` при загрузке.  
  
```  
Devenv.exe /ResetAddin MyAddin.Connect.MyAddin  
```  
  
## <a name="see-also"></a>См. также  
 [Персонализация интегрированной среды разработки Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)   
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)