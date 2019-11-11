---
title: Как настроить компьютер для разработки решений Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- prerequisites [Office development in Visual Studio]
- Office development in Visual Studio, installing tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: eb29dc4151bc457eb60ce836986817bc1b0137c9
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985967"
---
# <a name="how-to-configure-a-computer-to-develop-office-solutions"></a>Как настроить компьютер для разработки решений Office
  Для настройки компьютера разработчика таким образом, чтобы было можно использовать Microsoft Office Developer Tools в Visual Studio, следуйте инструкциям в этой статье. Для выполнения следующих действий требуются права администратора на компьютере разработчика.

### <a name="to-configure-the-development-computer"></a>Настройка компьютера разработчика

1. Установите версию Visual Studio, которая содержит Office Developer Tools. Office Developer Tools устанавливаются по умолчанию. Если вы настраиваете установку Visual Studio, выбрав компоненты для установки, убедитесь, что во время установки выбран параметр **Microsoft Office средства для разработчиков** . Дополнительные сведения о версиях Visual Studio, включающих средства разработчика Office, см. в разделе [Настройка компьютера для разработки решений Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

2. Установите версию Office, которую поддерживают Office Developer Tools в Visual Studio. Дополнительные сведения см. [в статье Настройка компьютера для разработки решений Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

     Убедитесь, что вы также устанавливаете основные сборки взаимодействия для нужной версии Office. Основные сборки взаимодействия устанавливаются вместе с Office по умолчанию. При изменении программы установки Office убедитесь, что для нужных приложений выбрана функция **поддержки программирования .NET** .

3. Если у вас установлена английская версия Visual Studio, но используются параметры, отличные от английского, для Windows можно установить [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] языковой пакет, чтобы видеть [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] сообщения на том же языке, что и Windows. Неанглоязычные версии Visual Studio автоматически устанавливают языковой пакет. Языковой пакет доступен в [центре загрузки Майкрософт](https://www.microsoft.com/download/details.aspx?id=54246).

## <a name="see-also"></a>См. также

- [Начало работы &#40;с разработкой Office в Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Руководство. Установка распространяемого пакета среды выполнения Office Инструменты Visual Studio](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [Руководство. Установка основных сборок взаимодействия Office](../vsto/how-to-install-office-primary-interop-assemblies.md)
