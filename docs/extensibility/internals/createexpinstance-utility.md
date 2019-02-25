---
title: Служебная программа CreateExpInstance | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2c4f77d0eba4ca974522534c69d554af9d807a9d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56597443"
---
# <a name="createexpinstance-utility"></a>Служебная программа CreateExpInstance
Используйте **CreateExpInstance** служебная программа для создания, сброс или удаление экспериментальный экземпляр Visual Studio. Экспериментальный экземпляр можно использовать для отладки и тестирования расширений Visual Studio без изменения базовой продукта.

## <a name="syntax"></a>Синтаксис

```
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix
```

## <a name="parameters"></a>Параметры
 **Или создайте** создает экспериментальный экземпляр.

 **/ Сбросить** удаляет экспериментальный экземпляр, а затем создает новый.

 **/ Очистка** удаляет экспериментальный экземпляр.

 **/ VSInstance** имя каталога, содержащего базовый экземпляр Visual Studio для копирования.

 **/ RootSuffix** суффикс для добавления к имени каталога экспериментальный экземпляр.

## <a name="remarks"></a>Примечания
 При работе в расширение Visual Studio, можно нажать F5, чтобы открыть экспериментальный экземпляр по умолчанию и установить текущего модуля. При наличии экспериментальный экземпляр Visual Studio создает один, который содержит настройки по умолчанию.

 По умолчанию расположение экспериментального экземпляра зависит от номера версии Visual Studio. Например, Visual Studio 2015, расположен в расположении *%localappdata%\Microsoft\VisualStudio\14.0Exp\\*. Все файлы в каталоге, считаются частью этого экземпляра. Экспериментальные дополнительных экземпляров не будет загружен в Visual Studio до изменения имени каталога в расположение по умолчанию.

 Visual Studio не осуществляет доступ к системного реестра при его открытии в экспериментальном экземпляре. Это отличается от более ранних версиях Visual Studio, в котором используется экспериментальная версия куст реестра.

 **CreateExpInstance** заменяет программу **VsRegEx** служебной программы.

 В следующем примере сбрасывается в экспериментальном экземпляре Visual Studio по умолчанию:

 **/ Reset CreateExpInstance.exe /VSInstance = 14.0/rootsuffix = Exp**

## <a name="see-also"></a>См. также
- [Пакеты VSPackage](../../extensibility/internals/vspackages.md)