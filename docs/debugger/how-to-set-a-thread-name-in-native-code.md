---
title: Установка имен потока в машинном коде | Документация Майкрософт
description: Установка имени потока в машинном коде во время отладки многопоточного приложения в Visual Studio. Именование потоков позволяет отслеживать их в окне "Потоки".
ms.custom: SEO-VS-2020
ms.date: 12/17/2018
ms.topic: how-to
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
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 024926123e8a9967947d11635558eb6ea06077cb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921672"
---
# <a name="how-to-set-a-thread-name-in-native-code"></a>Практическое руководство. Установка имени потока в машинном коде
Именование потоков можно выполнить в любом выпуске Visual Studio. Именование потоков позволяет находить необходимые потоки в окне **Потоки** при отладке выполняемого процесса. Кроме того, понятные имена потоков удобны при выполнении проверки аварийного дампа и анализа данных по производительности с применением различных инструментов.

## <a name="ways-to-set-a-thread-name"></a>Способы задания имени для потока

Имя для потока можно задать одним из двух способов. Во-первых, с помощью функции [SetThreadDescription](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreaddescription). Во-вторых, создав определенное исключение, когда отладчик Visual Studio подключается к процессу. Каждый подход имеет свои преимущества и недостатки. Функция `SetThreadDescription` поддерживается, начиная с Windows 10 версии 1607 или с Windows Server 2016.

Следует отметить, что при необходимости можно использовать сразу _оба_ подхода, так как механизмы их работы независимы друг от друга.

### <a name="set-a-thread-name-by-using-setthreaddescription"></a>Задание имени для потока с помощью функции `SetThreadDescription`

Преимущества:
* Имена потоков отображаются при отладке в Visual Studio независимо от того, был ли отладчик присоединен к процессу во время вызова функции SetThreadDescription.
* Имена потоков отображаются при выполнении отладки после аварийного завершения путем загрузки аварийного дампа в Visual Studio.
* Имена потоков отображаются и при работе с другими средствами, такими как отладчик [WinDbg](/windows-hardware/drivers/debugger/debugger-download-tools) и анализатор производительности [Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer).

Предупреждения:
* Имена потоков отображаются только в Visual Studio 2017 версии 15.6 и более поздних версий.
* При отладке файла аварийного дампа после аварийного завершения имена потоков отображаются только в том случае, если сбой произошел в Windows 10 версии 1607, Windows Server 2016 или более поздних версиях Windows.

*Пример.*

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

### <a name="set-a-thread-name-by-throwing-an-exception"></a>Задание имени для потока путем создания исключения

Другой способ задания имени для потока в программе — это передача желаемого имени потока в отладчик Visual Studio путем создания специально настроенного исключения.

Преимущества:
* Работает во всех версиях Visual Studio.

Предупреждения:
* Работает только в том случае, если отладчик был подключен в момент применения метода исключений.
* Имена потоков, заданные с помощью этого метода, не будут доступны в дампах или средствах анализа производительности.

*Пример.*

Представленная ниже функция `SetThreadName` демонстрирует метод исключений. Обратите внимание на то, что имя потока автоматически копируется в поток, чтобы можно было освободить память для параметра `threadName` после того, как вызов функции `SetThreadName` будет завершен.

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

## <a name="see-also"></a>См. также
- [Отладка многопоточных приложений](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Просмотр данных в отладчике](../debugger/viewing-data-in-the-debugger.md)
- [Практическое руководство. Установка имени потока в управляемом коде](../debugger/how-to-set-a-thread-name-in-managed-code.md)
