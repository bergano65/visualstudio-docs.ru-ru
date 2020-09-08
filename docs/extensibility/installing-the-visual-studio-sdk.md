---
title: Установка пакета SDK для Visual Studio | Документация Майкрософт
ms.date: 07/12/2018
ms.topic: overview
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31df92b011336320d759461ed16ce2a3c8f61017
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905543"
---
# <a name="install-the-visual-studio-sdk"></a>Установка пакета SDK для Visual Studio

Пакет SDK для Visual Studio (пакет средств разработки программного обеспечения) — дополнительный компонент программы установки Visual Studio. Пакет SDK для VS можно установить и позже.

## <a name="install-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Установка пакета SDK для Visual Studio при установке Visual Studio

Чтобы включить пакет SDK для VS в установку Visual Studio, установите рабочую нагрузку **Разработка расширения Visual Studio** в разделе **Другие наборы инструментов**. Эта рабочая нагрузка установит пакет SDK для Visual Studio и необходимые компоненты. Дальнейшую настройку установки можно выполнить, выбрав или отменив выбор компонентов в представлении **Сводка** .

## <a name="install-the-visual-studio-sdk-after-installing-visual-studio"></a>Установка пакета SDK для Visual Studio после установки Visual Studio

Чтобы установить пакет SDK для Visual Studio после завершения установки Visual Studio, снова запустите установщик Visual Studio и выберите рабочую нагрузку **Разработка расширения Visual Studio**.

## <a name="install-the-visual-studio-sdk-from-a-solution"></a>Установка пакета SDK для Visual Studio из решения

Если вы открываете решение с проектом расширяемости без предварительной установки пакета SDK для VS, в диалоговом окне **Установка отсутствующей функции** вам будет предложено установить рабочую нагрузку **Разработка расширения Visual Studio**:

![Установка разработки расширения](../extensibility/media/install-extension-development.png "Установка разработки расширения")

## <a name="install-the-visual-studio-sdk-from-the-command-line"></a>Установка пакета SDK для Visual Studio из командной строки

Как и в случае с любой другой рабочей нагрузкой или компонентом Visual Studio, вы также можете установить рабочую нагрузку **Разработка расширения Visual Studio** (идентификатор: Microsoft.VisualStudio.Workload.VisualStudioExtension) из командной строки. Дополнительные сведения о соответствующих параметрах командной строки и общие инструкции по определению идентификаторов рабочей нагрузки или компонентов см. в разделе [Использование параметров командной строки для установки Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md).

Обратите внимание на то, что вам необходимо использовать установщик Visual Studio, соответствующий установленной версии Visual Studio. Например, если на компьютере установлен Visual Studio Enterprise, необходимо запустить установщик Visual Studio Enterprise (*vs_enterprise. exe*).
