---
title: Практическое руководство. Указание двоичного файла для запуска | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.property.itemlaunch
helpviewer_keywords:
- profiling tools, launching
- performance tools, launching
- performance sessions, launching
ms.assetid: ba77fcf4-8d78-49f1-b8f3-7dd0acf84306
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6f3a176ded749f640f2e37f27c9753ee1902772c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51777374"
---
# <a name="how-to-specify-the-binary-to-start"></a>Практическое руководство. Указание двоичного файла для запуска
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Для профилирования двоичных файлов, таких как библиотеки DLL, необходимо ввести сведения в диалоговом окне **Страницы свойств \<целевой объект>**. Эти сведения указывают расположение проекта DLL для вызывающего приложения.  
  
 **Требования**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
### <a name="to-specify-the-executable-to-start"></a>Указание исполняемого файла для запуска  
  
1.  В **обозревателе производительности** щелкните правой кнопкой мыши целевой двоичный файл и выберите пункт **Свойства**.  
  
2.  В диалоговом окне **Страницы свойств** щелкните **Запуск**.  
  
3.  Установите флажок **Переопределить свойства проекта**.  
  
4.  В текстовом поле **Исполняемый файл для запуска** укажите расположение файла.  
  
5.  В текстовом поле **Аргументы** укажите аргументы, необходимые для запуска приложения.  
  
6.  В текстовом поле **Рабочий каталог** укажите расположение каталога.  
  
7.  Нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Настройка сеансов анализа производительности](../profiling/configuring-performance-sessions.md)



