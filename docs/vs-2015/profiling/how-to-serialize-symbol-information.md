---
title: Практическое руководство. Сериализация сведений о символах | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Performance.General
helpviewer_keywords:
- profiling tools, serializing symbol information
- performance tools, serializing symbol information
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 04bce9383142ee6916fa7ade50feda072019f530
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47569369"
---
# <a name="how-to-serialize-symbol-information"></a>Практическое руководство. Сериализация сведений о символах
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: сериализация сведений о символах](https://docs.microsoft.com/visualstudio/profiling/how-to-serialize-symbol-information).  
  
Можно выполнить сериализацию символов, необходимых для анализа работы приложения. При сериализации символы добавляются в VSP-файл. Если вы добавите сведения о символах в VSP-файл, другие пользователи смогут анализировать отчет о производительности без доступа к исходным символам. Если символы не сериализованы, для анализа VSP-файла необходимо иметь исходные инструментированные EXE- и PDB-файлы.  
  
### <a name="to-automatically-serialize-symbol-information"></a>Автоматическая сериализация сведений о символах  
  
1.  В меню **Сервис** выберите пункт **Параметры**.  
  
     Откроется диалоговое окно **Параметры**.  
  
2.  Щелкните **Средства производительности**.  
  
3.  В разделе **Общие параметры** выберите **Автоматическая сериализация символьной информации**.  
  
## <a name="see-also"></a>См. также  
 [Настройка сеансов анализа производительности](../profiling/configuring-performance-sessions.md)   
 [Практическое руководство. Справочная информация о символах Windows](../profiling/how-to-reference-windows-symbol-information.md)   
 [Практическое руководство. Сохранение файлов проанализированного отчета](http://msdn.microsoft.com/en-us/0340ddde-caf4-48ac-8af3-d15dcdade556)



