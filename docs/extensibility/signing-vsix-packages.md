---
title: Подписывание пакетов VSIX | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 08a709b50dd61beb874ea4cb80ebfb92a8fcd49e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720055"
---
# <a name="signing-vsix-packages"></a>Подписывание пакетов VSIX
Сборки расширений не обязательно должны быть подписаны, прежде чем они смогут работать в Visual Studio, но это рекомендуется сделать.

 Если вы хотите защитить расширение и убедиться, что оно не было изменено, можно добавить цифровую подпись к пакету VSIX. Если VSIX подписан, установщик VSIX отобразит сообщение о том, что оно подписано, а также дополнительные сведения о самой сигнатуре. Если содержимое VSIX было изменено и VSIX еще не подписан, установщик VSIX покажет, что подпись недействительна. Установка не остановлена, но пользователь получает предупреждение.

> [!IMPORTANT]
> Начиная с Visual Studio 2015, пакеты VSIX, подписанные с помощью чего-либо, отличного от шифрования SHA256, будут идентифицированы как имеющие недопустимую подпись. Установка VSIX не заблокирована, но пользователь получит предупреждение.

## <a name="signing-a-vsix-with-vsixsigntool"></a>Подписывание VSIX с помощью Всикссигнтул
 Существует инструмент для подписи шифрования SHA256, доступный в [висуалстудиоекстенсибилити](http://www.nuget.org/profiles/VisualStudioExtensibility) на NuGet.org по адресу [всикссигнтул](http://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool).

#### <a name="to-use-the-vsixsigntool"></a>Использование Всикссигнтул

1. Добавьте VSIX в проект.

2. Щелкните правой кнопкой мыши узел проекта в обозреватель решений, выберите **Добавить &#124; Управление пакетами NuGet**.  Дополнительные сведения о NuGet и добавлении пакетов NuGet см. в разделах [Документация по NuGet](/NuGet) и [Пользовательский интерфейс диспетчера пакетов](/NuGet/Tools/Package-Manager-UI) .

3. Выполните поиск по запросу Всикссигнтул из Висуалстудиоекстенсибилити и установите пакет NuGet.

4. Теперь можно запустить Всикссигнтул из расположения локальных пакетов проекта. Сведения о сценарии подписывания (Всикссигнтул. exe/?) см. в справке командной строки средства.

   Например, чтобы подписать файл сертификата, защищенный паролем:

   Всикссигнтул. exe Sign/f \<certfile >/p \<password > \<VSIXfile >

## <a name="see-also"></a>См. также
- [Доставка расширений Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
