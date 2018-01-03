---
title: "Практическое руководство. Создание общего выходного каталога | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- output directory
- builds [Visual Studio], common directory
- common directory
ms.assetid: 1fcc2c48-07cb-4c4f-9556-36945e7dfc4e
caps.latest.revision: "7"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f45831618e7d685da1f50ae634770ef735a6ff78
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-build-to-a-common-output-directory"></a>Практическое руководство. Создание общего выходного каталога
По умолчанию [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] создает каждый проект в отдельной папки внутри решения. Вы можете изменить пути вывода сборки для проекта, чтобы принудительно поместить все выходные данные в одну папку.  
  
### <a name="to-place-all-solution-outputs-in-a-common-directory"></a>Помещение всех выходных данных решения в общий каталог  
  
1.  Щелкните один проект в решении.  
  
2.  В меню **Проект** выберите пункт **Свойства**.  
  
3.  В зависимости от типа проекта откройте вкладку **Компиляция** или **Сборка** и задайте в поле **Выходной путь** папку, которую хотите использовать для всех проектов в решении.  
  
4.  Повторите шаги 1–3 для всех проектов в решении.  
  
## <a name="see-also"></a>См. также  
 [Компилирование и сборка](../ide/compiling-and-building-in-visual-studio.md)   
 [Практическое руководство. Изменение выходного каталога сборки](../ide/how-to-change-the-build-output-directory.md)