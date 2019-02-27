---
title: 'Практическое: Установка имени потока в машинном коде | Документация Майкрософт'
ms.date: 12/17/2018
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- debugging [C++], threads
- SetThreadName function
- threading [Visual Studio], names
- thread names
- debugging [Visual Studio], threads
ms.assetid: c85d0968-9f22-4d69-87f4-acca2ae777b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 264ac57a0d159b9cdd2627d7a62372fa070e31de
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56715184"
---
# <a name="how-to-set-a-thread-name-in-native-code"></a>Практическое руководство. Установка имен потока в машинном коде
Именование потоков можно выполнить в любом выпуске Visual Studio. Именование потоков используется для идентификации потоков в **потоков** окно при отладке к выполняющемуся процессу. Задавать именованных потоков можно также полезно при выполнении последующего отладки с помощью проверки аварийных дампов, а также при анализе производительности собирает с помощью различных средств.

## <a name="ways-to-set-a-thread-name"></a>Способы задания имени потока

Существует два способа задания имени потока. Во-первых, с помощью [SetThreadDescription](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreaddescription) функции. Второй способ конкретного исключения при присоединении отладчика Visual Studio к процессу. Каждый подход имеет преимущества и предупреждения.

Следует отметить, что _оба_ подхода могут использоваться совместно, при необходимости, так как механизмы, по которым они работают независимо друг от друга.

### <a name="set-a-thread-name-by-using-setthreaddescription"></a>Установка имени потока с помощью `SetThreadDescription`

Преимущества:
* Имена потоков видны при отладке в Visual Studio, независимо от того, является ли отладчик был подключен к процессу, когда вызывается SetThreadDescription.
* Имена потоков видны при выполнении отладочного дампа, загрузив аварийного дампа в Visual Studio.
* Имена потоков доступны при использовании других средств, таких как [WinDbg](https://docs.microsoft.com/windows-hardware/drivers/debugger/debugger-download-tools) отладчика и [Windows Performance Analyzer](https://docs.microsoft.com/windows-hardware/test/wpt/windows-performance-analyzer) анализатор производительности.

Предупреждения:
* Имена потоков только отображаются в Visual Studio 2017 версии 15.6 и более поздних версий.
* Когда файл дампа после неустранимого сбоя отладка сбоя, имена потоков, только если уведомление о сбое был создан в Windows 10 версии 1607, Windows Server 2016 или более поздних версиях Windows.

*Пример:*

```C++
#include <windows.h>
#include <processthreadsapi.h>

int main()
{
    HRESULT r;
    r = SetThreadDescription(
        GetCurrentThread(),
        L"ThisIsMyThreadName!"
    );

    return 0;
}
```

### <a name="set-a-thread-name-by-throwing-an-exception"></a>Установка имени потока путем создания исключения

Еще один способ задания имени потока в программе — имя нужный поток пользователям отладчик Visual Studio, выдав исключение, специально настроенные.

Преимущества:
* Работает во всех версиях Visual Studio.

Предупреждения:
* Работает, только если во время в методе, основанной на исключении подключен отладчик.
* Имена потоков, задайте с помощью этого метода будет недоступен в дампы или средства анализа производительности.

*Пример:*

`SetThreadName` Показанная ниже функция демонстрирует этот подход на основе исключения. Обратите внимание, что имя потока будут автоматически скопированы в поток, таким образом, чтобы память для `threadName` параметр может быть освобожден после `SetThreadName` завершения вызова.

```C++
//
// Usage: SetThreadName ((DWORD)-1, "MainThread");
//
#include <windows.h>
const DWORD MS_VC_EXCEPTION = 0x406D1388;
#pragma pack(push,8)
typedef struct tagTHREADNAME_INFO
{
    DWORD dwType; // Must be 0x1000.
    LPCSTR szName; // Pointer to name (in user addr space).
    DWORD dwThreadID; // Thread ID (-1=caller thread).
    DWORD dwFlags; // Reserved for future use, must be zero.
} THREADNAME_INFO;
#pragma pack(pop)
void SetThreadName(DWORD dwThreadID, const char* threadName) {
    THREADNAME_INFO info;
    info.dwType = 0x1000;
    info.szName = threadName;
    info.dwThreadID = dwThreadID;
    info.dwFlags = 0;
#pragma warning(push)
#pragma warning(disable: 6320 6322)
    __try{
        RaiseException(MS_VC_EXCEPTION, 0, sizeof(info) / sizeof(ULONG_PTR), (ULONG_PTR*)&info);
    }
    __except (EXCEPTION_EXECUTE_HANDLER){
    }
#pragma warning(pop)
}
```

## <a name="see-also"></a>См. также раздел
- [Отладка многопоточных приложений](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Просмотр данных в отладчике](../debugger/viewing-data-in-the-debugger.md)
- [Практическое руководство. Установка имени потока в управляемом коде](../debugger/how-to-set-a-thread-name-in-managed-code.md)
