---
title: Справка API (Visual Studio Debugging) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], API reference
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a2df6d82099a927664620e19096107f283afada
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738179"
---
# <a name="api-reference-visual-studio-debugging"></a>Справочник API (отладка Visual Studio)
Справочный раздел включает в себя концептуальный обзор API, руководство, которое показывает синтаксис и использование для всех элементов API, а также ассортимент примеров кода. Все ссылки перечислены в алфавитном порядке по категориям.

 В следующей таблице `HRESULT` показаны общие значения, возвращенные методами.

|name|Описание|Значение|
|----------|-----------------|-----------|
|S_OK|Успешно.|0x00000000|
|E_UNEXPECTED|Непредвиденный сбой.|0x8000FFFF|
|E_NOTIMPL|Не реализовано.|0x80004001|
|E_OUTOFMEMORY|Недостаточно памяти для завершения операции.|0x8007000E|
|E_INVALIDARG|Один или несколько аргументов недействительны.|0x80070057|
|E_NOINTERFACE|Такой интерфейс не поддерживается.|0x80004002|
|E_POINTER|Недопустимый указатель.|0x80004003|
|E_HANDLE|Недействительная ручка.|0x80070006|
|E_ABORT|Операция аварийно завершена.|0x80004004|
|E_FAIL|Непредвиденный сбой.|0x80004005|
|E_ACCESSDENIED|Общий доступ отказано в ошибке.|0x80070005|

> [!NOTE]
> При [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] возврате `S_OK`метода отладки предполагается, что все указатели параметров являются действительными, то `S_OK` есть проверка не проводится на указателях параметра при возврате.
>
> [!NOTE]
> Недействительные `NULL` или «не» параметры могут привести к сбою IDE.

## <a name="see-also"></a>См. также
- [Интерфейсы](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [Вспомогательные пакеты SDK для отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Расширяемость отладчика Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
