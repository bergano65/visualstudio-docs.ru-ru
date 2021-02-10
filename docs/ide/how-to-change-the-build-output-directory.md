---
title: Практическое руководство. Изменение выходного каталога сборки
description: Узнайте, как можно указать расположение выходных данных проекта для каждой конфигурации (для отладки, выпуска или и того и другого).
ms.custom: SEO-VS-2020
ms.date: 05/15/2019
ms.technology: vs-ide-compile
ms.topic: how-to
helpviewer_keywords:
- output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 792175d7d2c168f75d20bce86675a1fcd8c47899
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875540"
---
# <a name="how-to-change-the-build-output-directory"></a>Практическое руководство. Изменение выходного каталога сборки

Вы можете указать расположение выходных данных проекта для каждой конфигурации (для отладки, выпуска или и того и другого).

## <a name="change-the-build-output-directory"></a>Изменение выходного каталога сборки

1. Чтобы открыть страницы свойств проекта, в **обозревателе решений** щелкните узел проекта правой кнопкой мыши и выберите пункт **Свойства**.

2. В зависимости от типа проекта выберите соответствующую вкладку.

   - Для C# выберите вкладку **Сборка**.
   - Для Visual Basic выберите вкладку **Компиляция**.
   - Для C++ или JavaScript выберите вкладку **Общие**.

3. В раскрывающемся списке конфигураций в верхней части окна выберите конфигурацию, расположение файла выходных данных которой нужно изменить (**Отладка**, **Выпуск** или **Все конфигурации**).

4. На странице найдите запись выходного пути&mdash; — она зависит от типа проекта.

   - **Выходной путь** для проектов C# и JavaScript
   - **Выходной путь сборки** для проектов Visual Basic
   - **Выходной каталог** для проектов Visual C++

   Введите путь (абсолютный или относительный для корневого каталога проекта), по которому будут созданы выходные данные, или нажмите кнопку **Обзор** чтобы перейти к этой папке.

   ![Выходной путь для проекта Visual Studio C#](media/output-path.png)
   
   > [!NOTE]
   > Для некоторых проектов в путь сборки по умолчанию включаются платформа и среда выполнения. Чтобы они не включались, в **обозревателе решений** щелкните узел проекта правой кнопкой мыши, выберите команду **Изменить файл проекта** и добавьте следующее:
   > ```xml
   > <PropertyGroup>
   >   <AppendTargetFrameworkToOutputPath>false</AppendTargetFrameworkToOutputPath>
   >   <AppendRuntimeIdentifierToOutputPath>false</AppendRuntimeIdentifierToOutputPath>
   > </PropertyGroup>
   > ```

> [!TIP]
> Если выходные данные не создаются в указанном расположении, убедитесь, что выполняется сборка соответствующей конфигурации (например, **Отладка** или **Выпуск**), выбрав ее в строке меню Visual Studio.
>
> ![Средство выбора конфигурации "Сборка" в Visual Studio 2019](media/build-configuration-chooser.png)

## <a name="see-also"></a>См. также раздел

- Сведения о [странице сборки в конструкторе проектов (C#)](../ide/reference/build-page-project-designer-csharp.md)
- Сведения о [странице свойств "Общие" (проект)](/cpp/build/reference/general-property-page-project)
- [Компиляция и сборка](../ide/compiling-and-building-in-visual-studio.md)
