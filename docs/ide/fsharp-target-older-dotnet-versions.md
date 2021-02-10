---
title: Указание предыдущих версий в качестве целевой платформы .NET Framework для F#
description: Узнайте об указании более старой версии .NET Framework в качестве целевой платформы при использовании F# в Visual Studio.
ms.date: 07/11/2018
ms.topic: troubleshooting
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
monikerRange: vs-2017
ms.openlocfilehash: fe9d87a5cdea04251d7ab30b6e9e0fed6b0c4b31
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945530"
---
# <a name="target-older-versions-of-net-f"></a>Указание предыдущих версий в качестве целевой платформы .NET (F#)

При попытке указать .NET Framework версии 2.0, 3.0 или 3.5 в проекте F#, когда Visual Studio установлен в Windows 8.1, может появиться следующая ошибка:

**Для этого проекта требуется среда выполнения F# 2.0, но эта среда выполнения не установлена.**

Известно, что эта ошибка возникает в следующих обстоятельствах:

- Visual Studio установлен в Windows 8.1.

- Перед установкой Visual Studio не была включена платформа .NET Framework 3.5.

- Проект предназначен для .NET Framework 2.0, 3.0 или 3.5.

При установке Visual Studio он обнаруживает установленные версии платформы .NET Framework. Visual Studio устанавливает среду выполнения F# 2.0 только в том случае, если установлена и включена платформа .NET Framework 3.5.

## <a name="resolve-the-error"></a>Устранение ошибки

Эту ошибку можно устранить следующими способами:

- Укажите более новую целевую версию .NET Framework.

- Включите .NET Framework 3.5 в Windows 8.1, а затем установите среду выполнения F# 2.0 путем восстановления установки Visual Studio. Для этого выполните следующие действия.

### <a name="to-enable-the-net-framework-35-on-windows-81"></a>Включение .NET Framework 3.5 в Windows 8.1

1. На **начальном экране** введите **Панель управления**.

   При вводе под заголовком **Приложения** появляется значок **Панель управления**.

2. Выберите значок **Панель управления**, далее значок **Программы**, а затем ссылку **Включение или отключение компонентов Windows**.

3. Убедитесь, что флажок **.NET Framework 3.5 (включает .NET 2.0 и 3.0)** установлен, а затем нажмите кнопку **ОК**. Устанавливать флажки каких-либо дочерних узлов для включения дополнительных компонентов платформы .NET Framework не требуется.

   Платформа .NET Framework 3.5 включена, если это не было сделано ранее.

### <a name="to-install-the-f-20-runtime"></a>Установка среды выполнения F# 2.0

Выполните [действия для восстановления Visual Studio](../install/repair-visual-studio.md).

## <a name="see-also"></a>См. также раздел

- [Руководство по языку F# (.NET Framework)](/dotnet/fsharp/)
- [Язык F# в Visual Studio](fsharp-visual-studio.md)
