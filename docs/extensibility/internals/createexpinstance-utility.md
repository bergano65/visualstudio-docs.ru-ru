---
title: Утилита CreateExpInstance (англ.) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6a6b302976495e6067fad14317856cda4ac4625f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709245"
---
# <a name="createexpinstance-utility"></a>Утилита CreateExpInstance
Используйте утилиту **CreateExpInstance** для создания, сбросить или удалить экспериментальный экземпляр Visual Studio. Экспериментальный экземпляр можно использовать для отладки и тестирования расширений Visual Studio без изменения базового продукта.

## <a name="syntax"></a>Синтаксис

```
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix
```

## <a name="parameters"></a>Параметры
 **/Создание** Создает экспериментальный экземпляр.

 **/Перезагрузка** Удаляет экспериментальный экземпляр, а затем создает новый.

 **/Чистый** Удаляет экспериментальный экземпляр.

 **/VSInstance** Название каталога, содержащего базовый экземпляр Visual Studio для копирования.

 **/RootSuffix** Суффикс для придатка к названию каталога экспериментальных экземпляров.

## <a name="remarks"></a>Примечания
 Когда вы работаете над расширением Visual Studio, вы можете нажать F5, чтобы открыть экспериментальный экземпляр по умолчанию и установить текущее расширение. Если экспериментальный экземпляр недоступен, Visual Studio создает экземпляр, который имеет настройки по умолчанию.

 Расположение экспериментального экземпляра по умолчанию зависит от номера версии Visual Studio. Например, для Visual Studio 2015, местоположение *%localappdata% »Microsoft-VisualStudio »14.0Exp\\*. Все файлы в расположении каталога считаются частью этого экземпляра. Любые дополнительные экспериментальные экземпляры не будут загружены Visual Studio, если имя каталога не будет изменено на местоположение по умолчанию.

 Visual Studio не получает доступа к реестру системы при открытии экспериментального экземпляра. Это отличается от более ранних версий Visual Studio, в которой использовалась экспериментальная версия реестра улья.

 Утилита **CreateExpInstance** заменяет утилиту **VsRegEx.**

 Следующий пример сбрасывает экспериментальный экземпляр Visual Studio по умолчанию:

 **CreateExpInstance.exe /Перезагрузка /VSInstance-14.0 /RootSuffix-Exp**

## <a name="see-also"></a>См. также
- [Пакеты VSPackage](../../extensibility/internals/vspackages.md)
