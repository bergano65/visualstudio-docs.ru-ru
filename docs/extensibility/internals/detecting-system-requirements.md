---
title: Определение требований к системе | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c65df25645a13f58dce9ddec69acf6834a77210f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63420709"
---
# <a name="detect-system-requirements"></a>Определить требования к системе
Пакет VSPackage не может работать, если не установлена среда Visual Studio. При использовании установщика Windows для управления установкой вашего VSPackage, можно настроить программу установки, чтобы обнаруживать наличие установленного Visual Studio. Кроме того, можно также настроить для проверки системы другие требования, например, на конкретную версию Windows или определенный объем ОЗУ.

## <a name="detect-visual-studio-editions"></a>Обнаружить выпуски Visual Studio
 Чтобы определить, установлен ли выпуск Visual Studio, убедитесь, что значение **установить** реестра *(REG_DWORD) 1* в соответствующую папку, перечисленных в следующей таблице. Обратите внимание, что иерархия выпуски Visual Studio:

1. Предприятие

2. Professional

3. Сообщество

При установке более нового выпуска, разделы реестра для этого выпуска также добавляются как и для более ранних версий. То есть, если установлен выпуск Enterprise, **установить** ключ имеет значение *1* для предприятия, а также в выпусках Professional и Community. Таким образом необходимо проверить только для самой последней версии, что нужно.

> [!NOTE]
> 32-разрядные ключи в 64-разрядной версии редактора реестра, указанных в списке **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\\**. Visual Studio приведены в разделе **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\\**.

|Продукт|Ключ|
|-------------|---------|
|Visual Studio Enterprise|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|
|Оболочка Visual Studio 2015 (интегрированная и изолированная)|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|

## <a name="detect-when-visual-studio-is-running"></a>Обнаружить, когда выполняется Visual Studio
 Не удается зарегистрировать VSPackage правильно, если Visual Studio выполняется в том случае, когда объект VSPackage установлен. Установщик должен определять, когда выполняется Visual Studio и отклонять для установки программы. Установщик Windows не позволяет использовать записи таблицы для включения такого обнаружения. Вместо этого необходимо создать настраиваемое действие, следующим образом: Используйте `EnumProcesses` функции для обнаружения *devenv.exe* обработки, а затем либо установите свойство установщика, который используется в условии запуска или условию отображать диалоговое окно, которое предлагает пользователю закрыть Visual Studio.

## <a name="see-also"></a>См. также
- [Установка пакетов VSPackage с помощью установщика Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)