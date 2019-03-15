---
title: Практическое руководство. Настройка компьютера для разработки решений Office
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
ms.openlocfilehash: 9ab7ffdf6e9323b3d4ee67b2bf237b271abb1a7d
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/14/2019
ms.locfileid: "57869351"
---
# <a name="how-to-configure-a-computer-to-develop-office-solutions"></a>Практическое руководство. Настройка компьютера для разработки решений Office
  Для настройки компьютера разработчика таким образом, чтобы было можно использовать Microsoft Office Developer Tools в Visual Studio, следуйте инструкциям в этой статье. Для выполнения следующих действий требуются права администратора на компьютере разработчика.

### <a name="to-configure-the-development-computer"></a>Настройка компьютера разработчика

1.  Установите версию Visual Studio, которая содержит Office Developer Tools. Office Developer Tools устанавливаются по умолчанию. Если вы настраиваете установку Visual Studio, выбрав какие возможности нужно установить, убедитесь, что **инструменты разработчика Microsoft Office** выбирается во время установки. Дополнительные сведения о версиях Visual Studio, которые включают установку средств разработчика Office, см. в разделе [Настройка компьютера для разработки решений Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

2.  Установите версию Office, которую поддерживают Office Developer Tools в Visual Studio. Дополнительные сведения см. в разделе [Настройка компьютера для разработки решений Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

     Убедитесь, что вы также устанавливаете основные сборки взаимодействия для нужной версии Office. Основные сборки взаимодействия устанавливаются вместе с Office по умолчанию. Если вы изменяете настройки установки Office, убедитесь, что **программируемости .NET** выбран для приложений, вы будете работать.

3.  Если у английскую версию Visual Studio, но использовать неанглоязычные параметры для Windows, можно установить [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] языковой пакет для просмотра [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] сообщений в языке Windows. Неанглоязычные версии Visual Studio автоматически устанавливают языковой пакет. Языковой пакет доступен из [центра загрузки Майкрософт](http://go.microsoft.com/fwlink/?LinkId=140386).

## <a name="see-also"></a>См. также

- [Начало работы &#40;разработка решений Office в Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Практическое руководство. Установка средств Visual Studio для распространяемого пакета среды выполнения Office](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [Практическое руководство. Установка основных сборок взаимодействия Office](../vsto/how-to-install-office-primary-interop-assemblies.md)
