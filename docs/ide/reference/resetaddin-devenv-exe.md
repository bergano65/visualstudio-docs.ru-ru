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
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 826740ff2c56f50426d51e91fe9ccf8cdcb99081
ms.contentlocale: ru-ru
ms.lasthandoff: 05/24/2017

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
 [Персонализация интегрированной среды разработки Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)   
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)
