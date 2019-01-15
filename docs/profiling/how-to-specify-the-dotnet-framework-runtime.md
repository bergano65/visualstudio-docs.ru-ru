---
title: Как выполнить Определение среды выполнения .NET Framework | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools, .NET Framework versions
- .NET Framework versions,profililng
ms.assetid: d39f3579-719a-4f47-a97d-5b4232fe4c64
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 6baa0e37acb4ba24d0622ad27fe84c47e84da59d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53911017"
---
# <a name="how-to-specify-the-net-framework-runtime"></a>Как выполнить Определение среды выполнения .NET Framework

В выпуске [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)] можно составлять приложения из модулей, построенных с помощью разных версий среды выполнения [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. По умолчанию средства профилирования Visual Studio обрабатывают первую среду выполнения, загруженную приложением. Можно указать среду выполнения для профилирования при запуске приложения с помощью профилировщика и при подключении профилировщика к уже запущенному приложению.

## <a name="to-specify-the-net-framework-run-time-to-profile-when-starting-an-application-with-the-profiler"></a>Указание профилируемой среды выполнения .NET Framework при запуске приложения с помощью профилировщика

1. В **обозревателе производительности** щелкните правой кнопкой мыши сеанс анализа производительности, выберите пункт **Свойства**, а затем **Дополнительно**.

     В списке **Целевая версия CLR** отображается **Автоматически** и версия среды выполнения [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], которая установлена на компьютере.

2. Выполните одно из следующих действий.

    - Выберите версию среды CLR для профилирования.

    - Щелкните пункт **Автоматически**, чтобы выполнить профилирование первой версии, загруженной приложением.

## <a name="to-specify-the-net-framework-run-time-to-profile-when-attaching-the-profiler-to-an-application"></a>Указание профилируемой среды выполнения .NET Framework при подключении профилировщика к приложению

1. В меню **Анализ** наведите указатель мыши на пункт **Профилировщик** и щелкните **Присоединить/отсоединить**.

2. В диалоговом окне **Присоединить профилировщик к процессу** щелкните процесс, который необходимо профилировать.

     В списке **Целевая версия CLR** отображается **Автоматически** и версии среды выполнения [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], установленные на компьютере.

3. Выполните одно из следующих действий.

    - Выберите версию среды CLR для профилирования.

    - Щелкните **Автоматически** для профилирования версии, загружаемой при подключении профилировщика к приложению.