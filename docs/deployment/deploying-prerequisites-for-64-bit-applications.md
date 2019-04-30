---
title: Предварительные условия для 64-разрядных приложений развертывания | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [Visual Studio], 64-bit
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- 64-bit applications [Visual Studio]
ms.assetid: 87399e20-5510-41e4-b5b7-4a87c5773f21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c70b58577f8aa6e391215658afb7f8fa43c9bb5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62928892"
---
# <a name="deploy-prerequisites-for-64-bit-applications"></a>Предварительные условия для развертывания 64-разрядных приложений
Развертывание приложений ClickOnce поддерживает установку приложений на 64-разрядные платформы. Целевыми платформами являются **x86** для 32-разрядных платформ, **x64** для машин, поддерживающих наборы инструкций AMD64 и EM64T, а также **Itanium** для 64-разрядного процессора Itanium.

## <a name="prerequisites"></a>Предварительные требования
 В следующей таблице перечислены распространяемые компоненты, которые можно использовать в качестве необходимых компонентов для установки 64-разрядных приложений.

 Если вы выбрали необходимый компонент, не включающий 64-разрядные элементы, система выдаст предупреждение о том, что выбранные пакеты недоступны для 64-разрядных платформ.

| Распространяемые компоненты | Поддержка x64 | Поддержка IA64 |
| - |-------------|--------------|
| [!INCLUDE[vsto_runtime](../deployment/includes/vsto_runtime_md.md)] | Да | Нет |
| Библиотеки среды выполнения Visual C++ 2010 (IA64) | Нет | Да |
| Библиотеки времени выполнения Visual C++ 2010 (x64) | Да | Нет |
| Microsoft .NET Framework 4 (x86 и x64) | Да | |
| Клиентский профиль Microsoft .NET Framework 4 (x86 и x64) | Да | |

## <a name="see-also"></a>См. также
- [Развертывание приложений, служб и компонентов](../deployment/deploying-applications-services-and-components.md)
- [Практическое руководство. Установка необходимых компонентов для приложения ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [64-разрядные приложения](/dotnet/framework/64-bit-apps)