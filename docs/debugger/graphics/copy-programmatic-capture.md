---
title: Copy (программный захват) | Документация Майкрософт
description: Используйте метод Copy класса VsgDbg, чтобы скопировать содержимое активного файла журнала графики (.vsglog) в новый файл.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 126b1d7a2fa9064a343e7eadbe83dd1eeecccb83
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727848"
---
# <a name="copy-programmatic-capture"></a>Copy (программный захват)
Копирует содержимое активного файла журнала графики (.vsglog) в новый файл.

## <a name="syntax"></a>Синтаксис

```C++
void Copy(
  wchar_t const * szNewVSGLog
);
```

#### <a name="parameters"></a>Параметры
 `szNewVSGLog` Имя нового файла журнала графики.

## <a name="remarks"></a>Примечания
 Для копирования данных графики в новый файл должны быть уже захвачены какие-либо данные графики; в противном случае ничего не произойдет.