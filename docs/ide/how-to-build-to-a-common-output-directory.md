---
title: Практическое руководство. Создание общего выходного каталога
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- output directory
- builds [Visual Studio], common directory
- common directory
ms.assetid: 1fcc2c48-07cb-4c4f-9556-36945e7dfc4e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 12f45890224684ff2e4c411875ab61bdfb698cfb
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31942049"
---
# <a name="how-to-build-to-a-common-output-directory"></a>Практическое руководство. Создание общего выходного каталога

По умолчанию [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] создает каждый проект в отдельной папки внутри решения. Вы можете изменить пути вывода сборки для проекта, чтобы принудительно поместить все выходные данные в одну папку.

## <a name="to-place-all-solution-outputs-in-a-common-directory"></a>Помещение всех выходных данных решения в общий каталог

1.  Щелкните один проект в решении.

2.  В меню **Проект** выберите пункт **Свойства**.

3.  В зависимости от типа проекта откройте вкладку **Компиляция** или **Сборка** и задайте в поле **Выходной путь** папку, которую хотите использовать для всех проектов в решении.

4.  Повторите шаги 1–3 для всех проектов в решении.

## <a name="see-also"></a>См. также

- [Компиляция и сборка](../ide/compiling-and-building-in-visual-studio.md)
- [Практическое руководство. Изменение выходного каталога сборки](../ide/how-to-change-the-build-output-directory.md)