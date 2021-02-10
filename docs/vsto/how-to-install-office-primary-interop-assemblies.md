---
title: Руководство. Установка основных сборок взаимодействия Office
description: Узнайте, как установить Microsoft Office основные сборки взаимодействия (PIA) при установке Office.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- primary interop assemblies [Office development in Visual Studio], installing
- Office primary interop assemblies, installing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 432b2a74eb7ea4753cd110956c9dc9313e1a5d6e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934823"
---
# <a name="how-to-install-office-primary-interop-assemblies"></a>Руководство. Установка основных сборок взаимодействия Office
  При установке Office установите основные сборки взаимодействия Microsoft Office.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="to-install-the-pias-when-you-install-office"></a>Установка основных сборок взаимодействия при установке Office

1. Убедитесь в наличии версии .NET Framework не старше 2.0.

2. Установите Microsoft Office и убедитесь, что для приложений, которые требуется расширить, выбрана **Поддержка программирования .NET** (Эта функция включена в установку по умолчанию).

    > [!WARNING]
    > По умолчанию PIA внедряются в решение при его сборке, поэтому вам не нужно распространять PIA для пользователей в качестве необходимого компонента для использования надстройки или настройки VSTO.

## <a name="see-also"></a>См. также раздел
- [Основные сборки взаимодействия Office](../vsto/office-primary-interop-assemblies.md)
- [Пошаговое руководство. Назначение приложений Office через основные сборки взаимодействия](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Как настроить компьютер для разработки решений Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Руководство. Установка распространяемого пакета среды выполнения Office Инструменты Visual Studio](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Приступая к работе &#40;разработке решений Office в Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
