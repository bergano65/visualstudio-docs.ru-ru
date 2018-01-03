---
title: "Сбор данных взаимодействия уровней | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.performance.property.tierinteraction
helpviewer_keywords:
- Profiling Tools,ADO.NET profiling
- tier interaction profiling method
- Profiling Tools,tier-interaction method
- ADO.NET performance profiling
ms.assetid: 47a944c2-3098-497c-8fc7-e1f43d750bbc
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c12d279541e60353a9e6e4354a16870713498b66
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="collecting-tier-interaction-data"></a>Сбор данных взаимодействия уровней
Профилирование уровневого взаимодействия позволяет получить дополнительные сведения о времени выполнения функций многоуровневых приложений, взаимодействующих с базой данных посредством служб ADO.NET. Данные собираются только для синхронных вызовов функций.  
  
 **Выпуски Visual Studio**  
  
 Данные профилирования уровневого взаимодействия можно собирать с помощью Visual Studio Ultimate, Visual Studio Premium или Visual Studio Professional. Однако данные профилирования уровневого взаимодействия можно просматривать только в VS Ultimate и VS Premium.  
  
 **Windows 8 и Windows Server 2012**  
  
 Чтобы собрать данные об уровневом взаимодействии на классических приложениях Windows 8 и приложениях Windows Server 2012, необходимо использовать метод инструментирования. Вы не можете собрать данные о взаимодействии уровней для приложений универсальной платформы Windows. См. раздел [Средства производительности в приложениях Windows 8 и Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md). Данные об уровневом взаимодействии можно включить во все методы профилирования на других поддерживаемых версиях Windows.  
  
 **Мастер производительности**  
  
 Из-за ошибки в мастере производительности, необходимо добавить параметр коллекции данных об уровневом взаимодействии в сеанс профилирования из Обозревателя производительности. Необходимо также добавить проект, исполняемый файл или веб-сайт к узлу целевого объекта в "Обозревателе производительности".  
  
### <a name="to-add-tier-interaction-data-to-a-profiling-run-by-using-the-performance-session-property-pages"></a>Добавление данных взаимодействия уровней в сеанс профилирования с помощью страниц свойств сеанса анализа производительности  
  
1.  В обозревателе производительности в контекстном меню выберите пункт **Свойства**.  
  
2.  Выберите страницу **Взаимодействия уровня** и установите флажок **Включить профилирование взаимодействия уровней**.  
  
3.  В обозревателе производительности выделите узел **Целевые объекты**, а затем укажите проект, исполняемый файл или веб-сайт, который необходимо профилировать.  
  
## <a name="see-also"></a>См. также  
 [Представление "Взаимодействия уровня"](../profiling/tier-interactions-view.md)