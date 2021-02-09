---
title: Создание пакета решения SharePoint с помощью задач MSBuild
description: Узнайте, как создавать, очищать и проверять пакет решений SharePoint (WSP-пакеты) с помощью задач MSBuild на компьютере разработки.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f4c1d2e986b6a810cc568efd9577be87a38fdefb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873545"
---
# <a name="how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks"></a>Инструкции. Создание пакета решения SharePoint с помощью задач MSBuild
  Вы можете выполнять сборку, очистку и проверку пакета SharePoint (*WSP*) с помощью задач MSBuild командной строки на компьютере разработки. Эти команды также можно использовать для автоматизации процесса сборки с помощью Team Foundation Server на компьютере построения.

## <a name="build-a-sharepoint-package"></a>Создание пакета SharePoint

#### <a name="to-build-a-sharepoint-package"></a>Построение пакета SharePoint

1. В меню **Пуск** Windows выберите пункт **все программы**—  >    >  **Командная строка**.

2. Перейдите в каталог, где находится проект SharePoint.

3. Введите следующую команду, чтобы создать пакет для проекта. Замените *projectFileName* именем проекта.

    ```cmd
    msbuild /t:Package ProjectFileName
    ```

     Например, можно выполнить одну из следующих команд для упаковки проекта SharePoint с именем ListDefinition1.

    ```cmd
    msbuild /t:Package ListDefinition1.vbproj
    msbuild /t:Package ListDefinition1.csproj
    ```

## <a name="clean-a-sharepoint-package"></a>Очистить пакет SharePoint

#### <a name="to-clean-a-sharepoint-package"></a>Очистка пакета SharePoint

1. Откройте окно командной строки.

2. Перейдите в каталог, где находится проект SharePoint.

3. Введите следующую команду, чтобы очистить пакет для проекта. Замените *projectFileName* именем проекта.

    ```cmd
    msbuild /t:CleanPackage ProjectFileName
    ```

     Например, можно выполнить одну из следующих команд, чтобы очистить проект SharePoint с именем ListDefinition1.

    ```cmd
    msbuild /t:CleanPackage ListDefinition1.vbproj
    msbuild /t:CleanPackage ListDefinition1.csproj
    ```

## <a name="validate-a-sharepoint-package"></a>Проверка пакета SharePoint

#### <a name="to-validate-a-sharepoint-package"></a>Проверка пакета SharePoint

1. Откройте окно командной строки.

2. Перейдите в каталог, где находится проект SharePoint.

3. Введите следующую команду, чтобы проверить пакет для проекта. Замените *projectFileName* именем проекта.

    ```cmd
    msbuild /t:ValidatePackage ProjectFileName
    ```

     Например, можно выполнить одну из следующих команд для проверки проекта SharePoint с именем ListDefinition1.

    ```cmd
    msbuild /t:ValidatePackage ListDefinition1.vbproj
    msbuild /t:ValidatePackage ListDefinition1.csproj
    ```

## <a name="set-properties-in-a-sharepoint-package"></a>Задание свойств в пакете SharePoint

#### <a name="to-set-a-property-in-a-sharepoint-package"></a>Задание свойства в пакете SharePoint

1. Откройте окно командной строки.

2. Перейдите в каталог, где находится проект SharePoint.

3. Введите следующую команду, чтобы задать свойство в пакете для проекта. Замените *PropertyName* свойством, которое необходимо задать.

    ```cmd
    msbuild /property:PropertyName=Value
    ```

     Например, можно выполнить следующую команду, чтобы установить уровень предупреждений.

    ```cmd
    msbuild /property:WarningLevel = 2
    ```

## <a name="see-also"></a>См. также раздел
- [Создание компонентов SharePoint](../sharepoint/creating-sharepoint-features.md)
- [Руководство. Настройка компонента SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Как добавлять и удалять элементы в функциях SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
