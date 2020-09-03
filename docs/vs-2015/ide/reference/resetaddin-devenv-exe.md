---
title: -ResetAddin (devenv.exe) | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- disable addin
- addin state
- reset addin
ms.assetid: 9e339c8d-d768-4d86-8f45-2f479fc8255b
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9958e6e9a540dce1a405df8991780600b8f4a702
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665603"
---
# <a name="resetaddin-devenvexe"></a>/ResetAddin (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Удаляет команды и интерфейс пользователя команд, связанный с указанной надстройкой.

## <a name="syntax"></a>Синтаксис

```
Devenv /ResetAddin AddIn
```

## <a name="arguments"></a>Аргументы
 `AddIn` Необязательный. Имя команды надстройки.

## <a name="remarks"></a>Remarks
 По умолчанию имя команды надстройки равно *\<AddInSolutionName>* . Connect<em>. \<AddInSolutionName> </em>и появляется в Connect.cs в качестве `commandName` параметра `Exec` метода. Имя команды также можно проверить, начав вводить имя надстройки в окне "Команды" Visual Studio. Функция Intellisense закончит ввод.

## <a name="example"></a>Пример
 Следующий пример запускает Visual Studio и предотвращает запуск надстройки `MyAddin` при загрузке.

```
Devenv.exe /ResetAddin MyAddin.Connect.MyAddin
```

## <a name="see-also"></a>См. также:
 [Настройка параметров разработки в](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3) [параметрах командной строки](../../ide/reference/devenv-command-line-switches.md) для Visual Studio devenv
