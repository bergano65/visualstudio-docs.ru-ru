---
title: Сериализация сведений о символах | Документация Майкрософт
description: Сведения о том, как выполнить сериализацию символов,необходимых для анализа работы приложения, а также о способе, с помощью которого сериализация символов добавляет символы в VSP-файл.
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- VS.ToolsOptionsPages.Performance.General
helpviewer_keywords:
- profiling tools, serializing symbol information
- performance tools, serializing symbol information
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: bb9e965fb1b863d7e5837fe45a5d832fadcbc5c7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907041"
---
# <a name="how-to-serialize-symbol-information"></a>Практическое руководство. Сериализация сведений о символах
Можно выполнить сериализацию символов, необходимых для анализа работы приложения. При сериализации символы добавляются в *VSP*-файл. Если вы добавите сведения о символах в *VSP*-файл, другие пользователи смогут анализировать отчет о производительности без доступа к исходным символам. Если символы не сериализованы, для анализа *VSP*-файла необходимо иметь исходные инструментированные *EXE*- и *PDB*-файлы.

### <a name="to-automatically-serialize-symbol-information"></a>Автоматическая сериализация сведений о символах

1. В меню **Сервис** выберите пункт **Параметры**.

     Откроется диалоговое окно **Параметры**.

2. Щелкните **Средства производительности**.

3. В разделе **Общие параметры** выберите **Автоматическая сериализация символьной информации**.

## <a name="see-also"></a>См. также
- [Настройка сеансов анализа производительности](../profiling/configuring-performance-sessions.md)
- [Практическое руководство. Справочная информация о символах Windows](../profiling/how-to-reference-windows-symbol-information.md)
- [Практическое руководство. Сохранение файлов проанализированного отчета](/previous-versions/visualstudio/visual-studio-2010/bb763106\(v\=vs.100\))
