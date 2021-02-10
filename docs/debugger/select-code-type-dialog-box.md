---
title: Диалоговое окно "Выбор типа кода" | Документация Майкрософт
description: Сведения о диалоговом окне "Выбор типа кода" в Visual Studio. Чтобы открыть это диалоговое окно, откройте диалоговое окно Присоединение к процессу и нажмите кнопку Выбрать.
ms.custom: SEO-VS-2020
ms.date: 06/12/2020
ms.topic: reference
f1_keywords:
- vs.debug.selectengines
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- debugging [Visual Studio], engine selection
- debugger, engine selection
- debugging engine selection dialog box
no-loc:
- Blazor WebAssembly
ms.assetid: 932269fe-94e3-43cb-8931-078f31afd177
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7fb7b7625e8e08e291f4f27606d03f9066828e0a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903496"
---
# <a name="select-code-type-dialog-box"></a>Диалоговое окно "Выбор типа кода"

Чтобы открыть это диалоговое окно, откройте диалоговое окно **Присоединение к процессу** и нажмите кнопку **Выбрать**.

**Автоматически определять тип кода для отладки** Соответствующий отладчик будет выбираться в зависимости от типа выполняемого кода.

**Выполнять отладку кода следующих типов:** В предоставленном списке выберите один или несколько типов кода, который планируете отлаживать. Это может оказаться полезным при [устранении ошибок присоединения](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md#BKMK_Troubleshoot_attach_errors). Этот параметр позволяет обнаруживать только те типы кода, которые вы хотите отладить.

::: moniker range=">=vs-2019"
- Blazor WebAssembly — Blazor WebAssembly на стороне клиента
- GPU — Программный эмулятор — Код C++, выполняемый в программном эмуляторе GPU
- JavaScript (Chrome) — Код JavaScript, выполняемый в Chrome
- JavaScript (Microsoft Edge — Chromium) — Код JavaScript, выполняемый в браузере Microsoft Edge (на основе Chromium) для Windows 10
- Отладчик JavaScript для CDP (версия 3) — Протокол Chrome DevTools версии 3, используемый для отладки в клиенте CDP
- Управляемый (CoreCLR) — .NET Core
- Управляемый (компиляция в машинный код) — Код C++/CLR
- Управляемый (версии 3.5, 3.0,2.0) — Код .NET Framework для .NET Framework 2.0 и последующих версий (до 3.5)
- Управляемый (версии 4.6, 4.5, 4.0) — Код .NET Framework для .NET Framework 4.0 и последующих версий
- Машинный — C/C++
- Отладка Node.js — Код, размещенный в среде выполнения Node.js
- Python — Python 
- Скрипт — определяет общий отладчик скриптов для JavaScript. Используйте более строгие параметры, если они применимы к вашему сценарию, например JavaScript (Chrome).
- T-SQL — Transact-SQL
- Unity — Unity
- Режим совместимости управляемого кода — определяет отладчик предыдущих версий для управляемого кода, который обычно используется в смешанном режиме отладки с кодом C++/CLR (включает режим "Изменить и продолжить" для смешанного режима) или поддерживает расширения для отладчика предыдущих версий. В большинстве сценариев отладки в смешанном режиме следует выбрать **Машинный** и соответствующие типы кода **Управляемый**, а не режим совместимости управляемого кода.
::: moniker-end

В большинстве случаев подключение нескольких отладчиков в одном сеансе отладки не поддерживается. Это можно сделать, запустив второй экземпляр Visual Studio.

## <a name="see-also"></a>См. также
- [Безопасность отладчика](../debugger/debugger-security.md)
- [Подключение к выполняющимся процессам](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
