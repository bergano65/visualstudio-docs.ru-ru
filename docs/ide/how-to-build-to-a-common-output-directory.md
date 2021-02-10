---
title: Практическое руководство. Создание общего выходного каталога
description: Узнайте, как можно изменить пути вывода сборки для проекта, чтобы принудительно поместить все выходные данные в одну папку.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: how-to
helpviewer_keywords:
- output directory
- builds [Visual Studio], common directory
- common directory
ms.assetid: 1fcc2c48-07cb-4c4f-9556-36945e7dfc4e
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2e2abb9a768621477465b753554c111126a5af98
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967622"
---
# <a name="how-to-build-to-a-common-output-directory"></a>Практическое руководство. Создание общего выходного каталога

По умолчанию [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] создает каждый проект в отдельной папки внутри решения. Вы можете изменить пути вывода сборки для проекта, чтобы принудительно поместить все выходные данные в одну папку.

## <a name="to-place-all-solution-outputs-in-a-common-directory"></a>Помещение всех выходных данных решения в общий каталог

1. Щелкните один проект в решении.

2. В меню **Проект** выберите **Свойства**.

3. В зависимости от типа проекта откройте вкладку **Компиляция** или **Сборка** и задайте в поле **Выходной путь** папку, которую хотите использовать для всех проектов в решении.

4. Повторите шаги 1–3 для всех проектов в решении.

## <a name="see-also"></a>См. также раздел

- [Компиляция и сборка](../ide/compiling-and-building-in-visual-studio.md)
- [Практическое руководство. Изменение выходного каталога сборки](../ide/how-to-change-the-build-output-directory.md)