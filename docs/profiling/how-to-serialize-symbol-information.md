---
title: Как выполнить Сериализация сведений о символах | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Performance.General
helpviewer_keywords:
- profiling tools, serializing symbol information
- performance tools, serializing symbol information
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3b88268ba0ed8b1c324eda08ec3db969e088f279
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62539258"
---
# <a name="how-to-serialize-symbol-information"></a>Как выполнить Сериализация сведений о символах
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