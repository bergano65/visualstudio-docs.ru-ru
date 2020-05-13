---
title: Установка Визуальной студии SDK (ru) Документы Майкрософт
ms.date: 07/12/2018
ms.topic: conceptual
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f391708abbd8a9b66f2dfd5aaa6559cb075910d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710345"
---
# <a name="install-the-visual-studio-sdk"></a>Установка пакета SDK для Visual Studio

Visual Studio SDK (Комплект разработки программного обеспечения) является дополнительной функцией в установке Visual Studio. Вы также можете установить VS SDK позже.

## <a name="install-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Установка Визуальной студии SDK в рамках установки Visual Studio

Чтобы включить VS SDK в установку Visual Studio, установите рабочую нагрузку на **разработку расширения Visual Studio** под **другими наборами инструментов.** Эта рабочая нагрузка установит Visual Studio SDK и необходимые предпосылки. Вы можете дополнительно настроить установку, выбрав или не выбрав компоненты из представления **Резюме.**

## <a name="install-the-visual-studio-sdk-after-installing-visual-studio"></a>Установка визуальной студии SDK после установки Visual Studio

Чтобы установить Visual Studio SDK после завершения установки Visual Studio, перезапустите установку Visual Studio и выберите рабочую нагрузку разработки **расширения Visual Studio.**

## <a name="install-the-visual-studio-sdk-from-a-solution"></a>Установка Визуальной студии SDK из решения

Если вы откроете решение с проектом расширения без предварительной установки VS SDK, вам будет предложено диалог **установки missing Feature** для установки рабочей нагрузки **разработки расширения Visual Studio:**

![Установка разработки расширения](../extensibility/media/install-extension-development.png "Установка разработки расширения")

## <a name="install-the-visual-studio-sdk-from-the-command-line"></a>Установка Визуальной студии SDK из командной строки

Как и в случае с любой рабочей нагрузкой или компонентом Visual Studio, вы также можете установить рабочую нагрузку на **разработку расширения Visual Studio** (ID: Microsoft.VisualStudio.Workload.VisualStudioExtension) из командной строки. Просмотрите [параметры командной строки для установки Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) для получения подробной информации о соответствующих коммутаторах командной строки и общих инструкциях по определению рабочей нагрузки или идентификаторов компонентов.

Обратите внимание, что вы должны использовать установку Visual Studio, которая соответствует установленной версии Visual Studio. Например, если на компьютере установлено Visual Studio Enterprise, необходимо запустить установку Visual Studio Enterprise *(vs_enterprise.exe).*
