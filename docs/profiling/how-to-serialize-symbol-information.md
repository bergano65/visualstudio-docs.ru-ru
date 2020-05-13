---
title: Практическое руководство. Сериализация сведений о символах | Документы Майкрософт
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
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 202c30b1786e7e3ddb27583ddaeda9180d680b53
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "74774891"
---
# <a name="how-to-serialize-symbol-information"></a>Практическое руководство. Сериализация сведений о символах
Можно выполнить сериализацию символов, необходимых для анализа работы приложения. При сериализации символы добавляются в *VSP*-файл. Если вы добавите сведения о символах в *VSP*-файл, другие пользователи смогут анализировать отчет о производительности без доступа к исходным символам. Если символы не сериализованы, для анализа *VSP*-файла необходимо иметь исходные инструментированные *EXE*- и *PDB*-файлы.

### <a name="to-automatically-serialize-symbol-information"></a>Автоматическая сериализация сведений о символах

1. В меню **Сервис** выберите команду **Параметры**.

     Откроется диалоговое окно **Параметры**.

2. Щелкните **Средства производительности**.

3. В разделе **Общие параметры** выберите **Автоматическая сериализация символьной информации**.

## <a name="see-also"></a>См. также раздел
- [Настройка сеансов анализа производительности](../profiling/configuring-performance-sessions.md)
- [Практическое руководство. Справочная информация о символах Windows](../profiling/how-to-reference-windows-symbol-information.md)
- [Практическое руководство. Сохранение файлов проанализированного отчета](/previous-versions/visualstudio/visual-studio-2010/bb763106\(v\=vs.100\))
