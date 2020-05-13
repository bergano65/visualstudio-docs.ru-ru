---
title: Обнаружение системных требований Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ab254df5d53f379704128d8860b8d7fe5655bae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708736"
---
# <a name="detect-system-requirements"></a>Обнаружение требований к системам
VSPackage не может функционировать, если Visual Studio не установлена. При использовании Microsoft Windows Installer для управления установкой VSPackage можно настроить установку, чтобы определить, установлена ли Visual Studio. Можно также настроить его для проверки системы на наличие других требований, например, конкретной версии Windows или определенного количества оперативной памяти.

## <a name="detect-visual-studio-editions"></a>Обнаружение визуальных версий studio
 Чтобы определить, установлено ли издание Visual Studio, убедитесь, что значение ключа реестра **Install** *(REG_DWORD) 1* в соответствующей папке, как указано в следующей таблице. Обратите внимание, что существует иерархия визуальных версий Studio:

1. Предприятие

2. Professional

3. Сообщество

При установке нового издания добавляются ключи реестра для этого издания, а также для более ранних изданий. То есть, если издание Enterprise установлено, ключ **Установки** установлен на *1* для предприятия, а также для профессиональных и общинных изданий. Поэтому вам нужно проверить только для самого последнего издания вам нужно.

> [!NOTE]
> В 64-битной версии редактора реестра 32-битные клавиши отображаются под **HKEY_LOCAL_MACHINE»SOFTWARE-Wow6432Node\\**. Визуальная студия ключи находятся под **HKEY_LOCAL_MACHINE»SOFTWARE-Wow6432Node»Microsoft-DevDiv'vs.'Servicing\\**.

|Продукт|Клавиши|
|-------------|---------|
|Visual Studio Enterprise|HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-DevDiv-vs-Servicing-14.0 "предприятие|
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE»-SOFTWARE-Microsoft-DevDiv-vs-Servicing-14.0'professional|
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-DevDiv-vs-Servicing-14.0"community|
|Visual Studio 2015 Shell (интегрированная и изолированная)|HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-DevDiv-vs-Servicing-14.0|

## <a name="detect-when-visual-studio-is-running"></a>Обнаружение, когда Visual Studio работает
 Ваш VSPackage не может быть зарегистрирован правильно, если Visual Studio работает при установке VSPackage. Установщик должен определить, когда Visual Studio работает, а затем отказаться от установки программы. Установка Windows не позволяет использовать записи таблицы для обеспечения такого обнаружения. Вместо этого необходимо создать пользовательское действие следующим `EnumProcesses` образом: используйте функцию для обнаружения процесса *devenv.exe,* а затем либо установите свойство установки, используемое в состоянии запуска, либо условно отобразите диалоговую коробку, которая побуждает пользователя закрыть Visual Studio.

## <a name="see-also"></a>См. также
- [Установка VSPackages с установкой Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
