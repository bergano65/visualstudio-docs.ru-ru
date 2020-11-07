---
title: Программирование с набором средств Visual Studio для Unity | Документы Майкрософт
description: Ознакомьтесь с примерами программирования с помощью API Инструментов Visual Studio для Unity (VSTU). Настройка файлов проекта, созданных в VSTU. Совместное использование обратного вызова журнала Unity с VSTU.
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.assetid: a5758cb0-e73b-45f5-8cae-c0eb40491026
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: c98a3cdbcece87ad5e8fbe0e91ae76f677494477
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2020
ms.locfileid: "94341411"
---
# <a name="program-visual-studio-tools-for-unity"></a>Программирование с инструментами Visual Studio для Unity
В этом разделе приведены примеры использования набора средств Visual Studio для Unity API.

## <a name="examples"></a>Примеры
 Ниже приведены некоторые примеры, показывающие, как можно использовать набор средств Visual Studio для API-интерфейсов Unity.

### <a name="customize-project-files-created-by-vstu"></a>Настройка файлов проекта, созданных в VSTU
 Набор средств Visual Studio для Unity обеспечивает обратный вызов в стиле Unity во время создания файла проекта. Чтобы узнать, как изменять файл проекта при его повторном создании, обратитесь к разделу [Пример. Создание файла проекта](./customize-project-files-created-by-vstu.md).

### <a name="share-the-unity-log-callback-with-vstu"></a>Совместное использование обратного вызова журнала Unity с VSTU
 Набор средств Visual Studio для Unity регистрирует обратный вызов журнала для потоковой передачи данных консоли Unity в Visual Studio. Если скрипты редактора также регистрируют обратный вызов журнала с Unity, обратный вызов VSTU может повлиять на его работу. Чтобы узнать, как можно совместно использовать обратный вызов журнала Unity с VSTU, обратитесь к разделу [Пример. Обратный вызов журнала](./share-the-unity-log-callback-with-vstu.md).
