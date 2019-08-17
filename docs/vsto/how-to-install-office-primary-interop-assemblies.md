---
title: Практическое руководство. Установка основных сборок взаимодействия Office
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- primary interop assemblies [Office development in Visual Studio], installing
- Office primary interop assemblies, installing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ee6755a2d795d2018136785986a5a346ddc07dc6
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551791"
---
# <a name="how-to-install-office-primary-interop-assemblies"></a>Практическое руководство. Установка основных сборок взаимодействия Office
  При установке Office установите основные сборки взаимодействия Microsoft Office.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="to-install-the-pias-when-you-install-office"></a>Установка основных сборок взаимодействия при установке Office

1. Убедитесь в наличии версии .NET Framework не старше 2.0.

2. Установите Microsoft Office и убедитесь, что для приложений, которые требуется расширить, выбрана **Поддержка программирования .NET** (Эта функция включена в установку по умолчанию).

    > [!WARNING]
    > По умолчанию PIA внедряются в решение при его сборке, поэтому вам не нужно распространять PIA для пользователей в качестве необходимого компонента для использования надстройки или настройки VSTO.

## <a name="see-also"></a>См. также
- [Основные сборки взаимодействия Office](../vsto/office-primary-interop-assemblies.md)
- [Практическое руководство. Целевые приложения Office через основные сборки взаимодействия](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Практическое руководство. Настройка компьютера для разработки решений Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Практическое руководство. Установка распространяемого пакета среды выполнения Office Инструменты Visual Studio](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [Общие сведения о &#40;разработке решений Office VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Начало работы &#40;с разработкой Office в Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
