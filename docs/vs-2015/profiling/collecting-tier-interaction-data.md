---
title: Сбор данных взаимодействия уровней | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.tierinteraction
helpviewer_keywords:
- Profiling Tools,ADO.NET profiling
- tier interaction profiling method
- Profiling Tools,tier-interaction method
- ADO.NET performance profiling
ms.assetid: 47a944c2-3098-497c-8fc7-e1f43d750bbc
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: abe38162f20fb73de04301e97974dc348d704b6f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54770896"
---
# <a name="collecting-tier-interaction-data"></a>Сбор данных взаимодействия уровней
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Профилирование уровневого взаимодействия позволяет получить дополнительные сведения о времени выполнения функций многоуровневых приложений, взаимодействующих с базой данных посредством служб ADO.NET. Данные собираются только для синхронных вызовов функций.  
  
 **Выпуски Visual Studio**  
  
 Данные профилирования уровневого взаимодействия можно собирать с помощью Visual Studio Ultimate, Visual Studio Premium или Visual Studio Professional. Однако данные профилирования уровневого взаимодействия можно просматривать только в VS Ultimate и VS Premium.  
  
 **Windows 8 и Windows Server 2012**  
  
 Чтобы собрать данные об уровневом взаимодействии на классических приложениях Windows 8 и приложениях Windows Server 2012, необходимо использовать метод инструментирования. Вы не можете собрать данные об уровневом взаимодействии для приложений для Магазина Windows. См. раздел [Средства производительности в приложениях Windows 8 и Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md). Данные об уровневом взаимодействии можно включить во все методы профилирования на других поддерживаемых версиях Windows.  
  
 **Мастер производительности**  
  
 Из-за ошибки в мастере производительности, необходимо добавить параметр коллекции данных об уровневом взаимодействии в сеанс профилирования из Обозревателя производительности. Необходимо также добавить проект, исполняемый файл или веб-сайт к узлу целевого объекта в "Обозревателе производительности".  
  
### <a name="to-add-tier-interaction-data-to-a-profiling-run-by-using-the-performance-session-property-pages"></a>Добавление данных взаимодействия уровней в сеанс профилирования с помощью страниц свойств сеанса анализа производительности  
  
1.  В обозревателе производительности в контекстном меню выберите пункт **Свойства**.  
  
2.  Выберите страницу **Взаимодействия уровня** и установите флажок **Включить профилирование взаимодействия уровней**.  
  
3.  В обозревателе производительности выделите узел **Целевые объекты**, а затем укажите проект, исполняемый файл или веб-сайт, который необходимо профилировать.  
  
## <a name="see-also"></a>См. также раздел  
 [Представление "Взаимодействия уровня"](../profiling/tier-interactions-view.md)
