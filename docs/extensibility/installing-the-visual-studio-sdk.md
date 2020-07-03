---
title: Установка пакета SDK для Visual Studio | Документация Майкрософт
ms.date: 07/12/2018
ms.topic: overview
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31df92b011336320d759461ed16ce2a3c8f61017
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905543"
---
# <a name="install-the-visual-studio-sdk"></a>Установка пакета SDK для Visual Studio

Пакет SDK для Visual Studio (пакет средств разработки программного обеспечения) является дополнительным компонентом программы установки Visual Studio. Кроме того, пакет SDK для VS можно установить позже.

## <a name="install-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Установка пакета SDK для Visual Studio в составе установки Visual Studio

Чтобы включить пакет VS SDK в установку Visual Studio, установите рабочую нагрузку **Разработка расширений Visual Studio** в разделе **другие наборы инструментов**. Эта Рабочая нагрузка установит пакет SDK для Visual Studio и необходимые компоненты. Можно дополнительно настроить установку, выбрав или отменив выбор компонентов в представлении " **Сводка** ".

## <a name="install-the-visual-studio-sdk-after-installing-visual-studio"></a>Установка пакета SDK для Visual Studio после установки Visual Studio

Чтобы установить пакет SDK для Visual Studio после завершения установки Visual Studio, повторно запустите установщик Visual Studio и выберите рабочую нагрузку " **Разработка расширений Visual Studio** ".

## <a name="install-the-visual-studio-sdk-from-a-solution"></a>Установка пакета SDK для Visual Studio из решения

Если вы откроете решение с проектом расширения среды без предварительной установки пакета VS SDK, появится диалоговое окно **Установка отсутствующего компонента** для установки рабочей нагрузки **разработки расширения Visual Studio** :

![Установить разработку расширений](../extensibility/media/install-extension-development.png "Установить разработку расширений")

## <a name="install-the-visual-studio-sdk-from-the-command-line"></a>Установка пакета SDK для Visual Studio из командной строки

Как и в случае с любой рабочей нагрузкой или компонентом Visual Studio, можно также установить рабочую нагрузку **разработки расширения Visual Studio** (идентификатор: Microsoft. VisualStudio. Рабочая нагрузка. висуалстудиоекстенсион) из командной строки. Дополнительные сведения о параметрах командной строки и общие инструкции по определению идентификаторов рабочей нагрузки или компонентов см. в статье [Использование параметров командной строки для установки Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) .

Обратите внимание, что необходимо использовать установщик Visual Studio, соответствующий установленной версии Visual Studio. Например, если на компьютере установлен Visual Studio Enterprise, необходимо запустить установщик Visual Studio Enterprise (*vs_enterprise.exe*).
