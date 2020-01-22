---
title: Управление конфигурациями сборок с применением параметров разработчика Visual Basic
ms.date: 11/21/2018
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- advanced build configurations
- building with Visual Basic developer settings (Visual Studio)
- debug builds
- release builds
ms.assetid: eaea6e0b-6c61-4869-8d63-d372c745a23c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5243223e554f8e31fe2ffa9d667c09d0a3e1dbc0
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115162"
---
# <a name="how-to-manage-build-configurations-with-visual-basic-developer-settings-applied"></a>Практическое руководство. Управление конфигурациями сборок с применением параметров разработчика Visual Basic

По умолчанию все расширенные параметры сборки скрыты при применении параметров разработчика Visual Basic. В этой статье объясняется, как включить эти параметры сборки вручную.

## <a name="enable-advanced-build-configurations"></a>Включение дополнительных конфигураций сборок

По умолчанию в параметрах разработчика Visual Basic возможность открыть диалоговое окно **диспетчера конфигураций**, как и списки **конфигураций** и **платформ** в [конструкторе проектов](../ide/reference/application-page-project-designer-visual-basic.md), скрыта.

1. В меню **Сервис** выберите пункт **Параметры**.

2. Разверните узел **Проекты и решения** и выберите **Общие**.

    > [!NOTE]
    > Узел **Общие** отображается, даже если не установлен флажок **Показать все параметры**. Если вы хотите просмотреть все доступные параметры, щелкните **Показать все параметры**.

3. Установите флажок **Показывать дополнительные конфигурации построения**.

4. Нажмите кнопку **ОК**.

     Теперь в меню **Сборка** можно выбрать пункт **Диспетчер конфигураций**, а списки **конфигураций** и **платформ** отображаются в **конструкторе проектов**.

## <a name="see-also"></a>См. также

- [Общие сведения о конфигурациях построения](../ide/understanding-build-configurations.md)
- [Компиляция и сборка](../ide/compiling-and-building-in-visual-studio.md)
- [Параметры среды](../ide/environment-settings.md)
