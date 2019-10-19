---
title: -Log (devenv.exe) | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f427edfe294605b7b2adcbb0889e48c4f37b6ba9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666845"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Регистрирует все действия в файле журнала для устранения неполадок. Этот файл отображается после вызова `devenv /log` по крайней мере один раз. Файл журнала по умолчанию:

 *%APPDATA%* \Microsoft\VisualStudio\\*Версия*\ActivityLog.xml

 где *Версия* — это версия Visual Studio. Однако можно указать альтернативный путь и имя файла.

## <a name="syntax"></a>Синтаксис

```
Devenv /log Path\NameOfLogFile
```

## <a name="remarks"></a>Примечания
 Этот ключ должен находиться в конце командной строки после всех других параметров.

 Журнал записывается для всех экземпляров Visual Studio, которые были активированы с ключом /log. Для экземпляров Visual Studio, которые были активированы без данного ключа, журнал не записывается.

## <a name="see-also"></a>См. также
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)
