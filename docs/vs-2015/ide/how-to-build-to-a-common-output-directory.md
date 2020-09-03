---
title: Практическое руководство. Создание общего выходного каталога | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- output directory
- builds [Visual Studio], common directory
- common directory
ms.assetid: 1fcc2c48-07cb-4c4f-9556-36945e7dfc4e
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f85ff51b93383d2deca409a00a3db130d52b5003
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645417"
---
# <a name="how-to-build-to-a-common-output-directory"></a>Практическое руководство. Создание общего выходного каталога
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

По умолчанию [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] создает каждый проект в отдельной папки внутри решения. Вы можете изменить пути вывода сборки для проекта, чтобы принудительно поместить все выходные данные в одну папку.

### <a name="to-place-all-solution-outputs-in-a-common-directory"></a>Помещение всех выходных данных решения в общий каталог

1. Щелкните один проект в решении.

2. В меню **Проект** выберите **Свойства**.

3. В зависимости от типа проекта откройте вкладку **Компиляция** или **Сборка** и задайте в поле **Выходной путь** папку, которую хотите использовать для всех проектов в решении.

4. Повторите шаги 1–3 для всех проектов в решении.

## <a name="see-also"></a>См. также:
 [Компиляция и построение](../ide/compiling-and-building-in-visual-studio.md) [: как изменить выходной каталог сборки](../ide/how-to-change-the-build-output-directory.md)
