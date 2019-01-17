---
title: Указание предыдущих версий в качестве целевой платформы .NET Framework для F#
description: Узнайте об указании более старой версии .NET Framework в качестве целевой платформы при использовании F# в Visual Studio.
ms.date: 07/11/2018
ms.prod: visual-studio-dev15
ms.topic: troubleshooting
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 4f5ef4e8b46681cc102a6678fcd4cb38f3e6f069
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53888080"
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

Выполните [действия для восстановления Visual Studio 2017](../install/repair-visual-studio.md).

## <a name="see-also"></a>См. также

- [Руководство по языку F# (.NET Framework)](/dotnet/fsharp/)
- [Язык F# в Visual Studio](fsharp-visual-studio.md)