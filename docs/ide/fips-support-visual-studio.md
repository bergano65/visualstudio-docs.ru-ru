---
title: Поддержка утвержденного режима работы FIPS 140-2 в Visual Studio
ms.date: 04/14/2020
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d06204fd1ef6ee2deb5eadc514af1ede8ae9bb6
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2020
ms.locfileid: "84180497"
---
# <a name="visual-studio-support-for-the-fips-140-2-approved-mode-of-operation"></a>Поддержка утвержденного режима работы FIPS 140-2 в Visual Studio

Начиная с [версии 16.4](/visualstudio/releases/2019/release-notes-v16.4/), Visual Studio 2019 поддерживает утвержденный режим работы согласно Федеральным стандартам обработки информации (FIPS), публикация 140-2 для Windows, Azure и .NET. Начиная с [версии 16.5](/visualstudio/releases/2019/release-notes-archive-v16.5), Visual Studio поддерживает утвержденный режим работы FIPS 140-2 при разработке [приложений C++, предназначенных для удаленной системы Linux](/cpp/linux/set-up-fips-compliant-secure-remote-linux-development/).

Чтобы настроить утвержденный режим работы FIPS 140-2 для Visual Studio, [установите .NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/net48), а затем включите параметр групповой политики **Системная криптография: использовать FIPS-совместимые алгоритмы для шифрования, хэширования и подписывания**.

Дополнительные сведения об утвержденном режиме работы FIPS 140-2 и о том, как включить его, см. в статье [Проверка FIPS 140-2](/windows/security/threat-protection/fips-140-validation/).

> [!NOTE]
> Инструменты разработки приложений для платформ не от Майкрософт, например для iOS или Android, могут не использовать алгоритмы, соответствующие стандартам FIPS. То же относится к включаемому в Visual Studio стороннему ПО или устанавливаемым вами расширениям. Кроме того, разработка решений [SharePoint](/sharepoint/security-for-sharepoint-server/federal-information-processing-standard-security-standards/) не поддерживает утвержденный режим работы FIPS 140-2.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения об утвержденном режиме работы FIPS 140-2 для Visual Studio и других продуктов и служб Майкрософт см. по следующим ссылкам.

- [Visual Studio. Настройка совместимой с FIPS безопасной удаленной разработки для Linux на C++](/cpp/linux/set-up-fips-compliant-secure-remote-linux-development/)
- [Windows. Системная криптография и использование FIPS-совместимых алгоритмов для шифрования, хэширования и подписывания](/windows/security/threat-protection/security-policy-settings/system-cryptography-use-fips-compliant-algorithms-for-encryption-hashing-and-signing)
- [.NET Core. Соответствие FIPS](/dotnet/standard/security/fips-compliance/)

## <a name="see-also"></a>См. также

[Защита приложений](securing-applications.md)
