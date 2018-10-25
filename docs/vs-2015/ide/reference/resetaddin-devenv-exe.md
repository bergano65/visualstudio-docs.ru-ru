---
title: -ResetAddin (devenv.exe) | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- disable addin
- addin state
- reset addin
ms.assetid: 9e339c8d-d768-4d86-8f45-2f479fc8255b
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f1b53a30845ca4b20372fb5a6e3552f31f3c1b60
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950528"
---
# <a name="resetaddin-devenvexe"></a>/ResetAddin (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Удаляет команды и интерфейс пользователя команд, связанный с указанной надстройкой.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Devenv /ResetAddin AddIn  
```  
  
## <a name="arguments"></a>Аргументы  
 `AddIn`  
 Необязательный. Имя команды надстройки.  
  
## <a name="remarks"></a>Примечания  
 По умолчанию имя команды надстройки — *\<AddInSolutionName>*.Connect<em>.\<AddInSolutionName></em>. Оно отображается в файле Connect.cs как параметр `commandName` метода `Exec`. Имя команды также можно проверить, начав вводить имя надстройки в окне "Команды" Visual Studio. Функция Intellisense закончит ввод.  
  
## <a name="example"></a>Пример  
 Следующий пример запускает Visual Studio и предотвращает запуск надстройки `MyAddin` при загрузке.  
  
```  
Devenv.exe /ResetAddin MyAddin.Connect.MyAddin  
```  
  
## <a name="see-also"></a>См. также  
 [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)



