---
title: 'Практическое: поиск процесса в представлении процессов | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Processes view
- processes, searching for
ms.assetid: 7cb97b37-4a95-4f1b-9eee-4910aa9c115b
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c187089c8aeec3b2c0409adbab1f262893720d87
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51735602"
---
# <a name="how-to-search-for-a-process-in-processes-view"></a>Практическое руководство. Поиск процесса в представлении процессов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно найти конкретный процесс в представлении процессов с помощью его процесса идентификатор или строку модуля в качестве критерия поиска. Можно также указать исходное направление поиска. Поля в диалоговом окне будут отображаться атрибуты выбранного процесса в дерево процесса.  
  
### <a name="to-search-for-a-process-in-processes-view"></a>Поиск процесса в представлении процессов  
  
1. Расположение окон, поэтому Spy ++ и действующая [представление процессов](../debugger/processes-view.md) окна являются видимыми.  
  
2. Из **поиска** меню, выберите **найти процесс**  
  
    [Диалоговое окно "Поиск процесса"](../debugger/process-search-dialog-box.md) открывает.  
  
3. Введите идентификатор процесса или строку модуля в качестве критерия поиска.  
  
4. Очистите все поля, для которых вы не хотите указать значения.  
  
   > [!TIP]
   >  Чтобы найти все процессы, принадлежащие модулю, снимите **процесс** объекта и введите имя модуля в **модуль** поле. Затем с помощью **Найти далее** для продолжения поиска.  
  
5. Выберите **вверх** или **вниз** для исходное направление поиска.  
  
6. Нажмите кнопку **ОК**.  
  
   Если найден процесс сопоставления, он выделяется в **представление "процесс"** окна.



