---
title: Практическое руководство. Сериализация сведений о символах | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Performance.General
helpviewer_keywords:
- profiling tools, serializing symbol information
- performance tools, serializing symbol information
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c4ea056c48525014fffad0243dfeb4dd40a8daa3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687016"
---
# <a name="how-to-serialize-symbol-information"></a>Практическое руководство. Сериализация сведений о символах
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно выполнить сериализацию символов, необходимых для анализа работы приложения. При сериализации символы добавляются в VSP-файл. Если вы добавите сведения о символах в VSP-файл, другие пользователи смогут анализировать отчет о производительности без доступа к исходным символам. Если символы не сериализованы, для анализа VSP-файла необходимо иметь исходные инструментированные EXE- и PDB-файлы.  
  
### <a name="to-automatically-serialize-symbol-information"></a>Автоматическая сериализация сведений о символах  
  
1. В меню **Сервис** выберите пункт **Параметры**.  
  
     Откроется диалоговое окно **Параметры**.  
  
2. Щелкните **Средства производительности**.  
  
3. В разделе **Общие параметры** выберите **Автоматическая сериализация символьной информации**.  
  
## <a name="see-also"></a>См. также:  
 [Настройка сеансов анализа производительности](../profiling/configuring-performance-sessions.md)   
 [Инструкции: справочные сведения о символах Windows](../profiling/how-to-reference-windows-symbol-information.md)   
 [Как сохранять проанализированные файлы отчетов](https://msdn.microsoft.com/0340ddde-caf4-48ac-8af3-d15dcdade556)
