---
title: "Практическое руководство. Создание общего выходного каталога | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "построения [Visual Studio], общий каталог"
  - "общий каталог"
  - "каталог вывода"
ms.assetid: 1fcc2c48-07cb-4c4f-9556-36945e7dfc4e
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# Практическое руководство. Создание общего выходного каталога
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

По умолчанию в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] каждый проект собирается отдельной папки внутри своего решения.  Можно изменить путь выхода проекта, чтобы все выходные файлы размещались в одной и той же папке.  
  
### Для размещения всех выходных файлов решения в одной папке  
  
1.  Щелкните один проект решения.  
  
2.  В меню **Проект** выберите пункт **Свойства**.  
  
3.  В зависимости от типа проекта перейдите либо на вкладку **Компиляция**, либо на вкладку **Построение** и укажите для параметра **Путь вывода** папку, которую будут использовать все проекты в решении.  
  
4.  Повторите шаги 1–3 для всех проектов решения.  
  
## См. также  
 [Построение приложений в Visual Studio](../ide/compiling-and-building-in-visual-studio.md)   
 [Практическое руководство. Изменение выходного каталога построения](../ide/how-to-change-the-build-output-directory.md)