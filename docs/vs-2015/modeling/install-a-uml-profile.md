---
title: Установка профиля UML | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, profiles
ms.assetid: 586f9ba5-4d01-4a1d-b001-32e2efaa4f24
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 89531fe0f2e912a6aabd962ab56ca7a24a7f3e20
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850654"
---
# <a name="install-a-uml-profile"></a>Установка профиля UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

С помощью профиля UML можно расширить возможности Visual Studio. Профиль позволяет добавлять стереотипы и дополнительные свойства в элементы, которые можно создавать в моделях UML. Чтобы узнать, какие версии Visual Studio поддерживают эту функцию, см. раздел [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Если вы получили модель UML, созданную с использованием профилей, некоторые свойства не будут отображаться, если эти профили не установлены.

 Профиль распространяется внутри расширения Visual Studio. Расширение также может содержать другие функции, такие как команды меню. Дополнительные сведения см. в разделе [Управление расширениями Visual Studio](https://msdn.microsoft.com/library/dd293638(VS.100).aspx).

### <a name="to-install-a-uml-profile-on-your-computer"></a>Установка профиля UML на компьютер

1. Профиль должен быть предоставлен в форме файла с расширением Visual Studio (`.vsix`). В одном файле могут содержаться и другие функции.

     Переместите файл `.vsix` в удобное место на компьютере.

2. Дважды щелкните файл `.vsix` в проводнике или откройте его в [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

3. В появившемся диалоговом окне нажмите кнопку **установить** .

4. Чтобы удалить или временно отключить расширение, откройте **Диспетчер расширений** в меню **Сервис** .

### <a name="to-uninstall-or-disable-a-profile-extension"></a>Удаление или отключение расширения профиля

1. В меню **Сервис** Visual Studio выберите пункт **Диспетчер расширений**.

2. Выберите расширение, которое требуется удалить, а затем нажмите кнопку **Отключить** или **Удалить**.

## <a name="see-also"></a>См. также раздел
 [Настройка модели с помощью профилей и стереотипов](../modeling/customize-your-model-with-profiles-and-stereotypes.md) [Определение профиля для расширения UML](../modeling/define-a-profile-to-extend-uml.md)
