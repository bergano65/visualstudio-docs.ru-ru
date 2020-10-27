---
title: Программирование с набором средств Visual Studio для Unity | Документы Майкрософт
description: Ознакомьтесь с примерами программирования с помощью API Инструментов Visual Studio для Unity (VSTU). Настройка файлов проекта, созданных в VSTU. Совместное использование обратного вызова журнала Unity с VSTU.
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: a5758cb0-e73b-45f5-8cae-c0eb40491026
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 0372cfd110df77867a683b27b17f92cd70ba75aa
ms.sourcegitcommit: 01c1b040b12d9d43e3e8ccadee20d6282154faad
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2020
ms.locfileid: "92039889"
---
# <a name="program-visual-studio-tools-for-unity"></a>Программирование с инструментами Visual Studio для Unity
В этом разделе приведены примеры использования набора средств Visual Studio для Unity API.

## <a name="examples"></a>Примеры
 Ниже приведены некоторые примеры, показывающие, как можно использовать набор средств Visual Studio для API-интерфейсов Unity.

### <a name="customize-project-files-created-by-vstu"></a>Настройка файлов проекта, созданных в VSTU
 Набор средств Visual Studio для Unity обеспечивает обратный вызов в стиле Unity во время создания файла проекта. Чтобы узнать, как изменять файл проекта при его повторном создании, обратитесь к разделу [Пример. Создание файла проекта](../cross-platform/customize-project-files-created-by-vstu.md).

### <a name="share-the-unity-log-callback-with-vstu"></a>Совместное использование обратного вызова журнала Unity с VSTU
 Набор средств Visual Studio для Unity регистрирует обратный вызов журнала для потоковой передачи данных консоли Unity в Visual Studio. Если скрипты редактора также регистрируют обратный вызов журнала с Unity, обратный вызов VSTU может повлиять на его работу. Чтобы узнать, как можно совместно использовать обратный вызов журнала Unity с VSTU, обратитесь к разделу [Пример. Обратный вызов журнала](../cross-platform/share-the-unity-log-callback-with-vstu.md).
