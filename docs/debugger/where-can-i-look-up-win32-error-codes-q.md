---
title: Где можно найти коды ошибок Win32? | Документы Майкрософт
description: 'Чтобы просмотреть код ошибки Win32, введите его в окне "Контрольные значения" или "Быстрая проверка". Пример: "0x80000004,hr". Определения кодов ошибок находятся в файле INCLUDE\WINERROR.H.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vc.errors
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- error codes, Win32
- Win32, error codes
ms.assetid: 8fb4ff42-b8eb-4152-b49e-b802d194b05e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 44a006be3b6ecad3ef723c00154354cb35df0049
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149291"
---
# <a name="where-can-i-look-up-win32-error-codes"></a>Где можно найти коды ошибок Win32?
WINERROR.H в папке INCLUDE стандартного дистрибутива содержит определения кодов ошибок для функций Win32 API.

 Кроме того, код ошибки можно посмотреть, введя код в окно **Контрольные значения** или в диалоговом окне **Быстрая проверка**. Пример:

`0x80000004,hr`

## <a name="see-also"></a>См. также
- [Вопросы и ответы по отладке машинного кода](../debugger/debugging-native-code-faqs.md)
- [Отладка машинного кода](../debugger/debugging-native-code.md)