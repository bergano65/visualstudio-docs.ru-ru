---
title: Исключение из Windows Information Protection
description: Сведения об исключении Visual Studio из Windows Information Protection, но с разрешением Visual Studio использовать корпоративные данные.
ms.custom: SEO-VS-2020
ms.date: 06/01/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6ff233b959b4ad691646c5e47c659b398b283b5c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897999"
---
# <a name="configure-visual-studio-as-a-wip-exempt-app"></a>Настройка Visual Studio как приложения, свободного от WIP

[Windows Information Protection](/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip) (WIP) помогает защитить корпоративные данные от утечки через такие приложения, как электронная почта, социальные сети и публичное облако, которые находятся вне зоны контроля организации. WIP обеспечивает защиту от случайной утечки данных на корпоративных и личных устройствах, не требуя внесения изменений в среду или другие приложения.

Приложения *с расширенными возможностями* для WIP должны предотвращать попадание корпоративных данных в незащищенные сетевые расположения и избегать шифрования персональных данных. Visual Studio не является приложением с расширенными возможностями, поэтому он не работает в средах с поддержкой WIP, пока вы не исключите его. Выполните действия, приведенные в этой статье, чтобы позволить Visual Studio функционировать на компьютере с поддержкой WIP.

## <a name="configure-vs-as-a-wip-exempt-app"></a>Настройка VS как приложения, свободного от WIP

Вы можете исключить Visual Studio из ограничений WIP, но сохранить для него возможность по-прежнему использовать корпоративные данные. Приложения, свободные от WIP, могут подключаться к корпоративным облачным ресурсам с помощью IP-адреса или имени узла. Шифрование не применяется, и приложение может получать доступ к локальным файлам.

Чтобы исключить Visual Studio из WIP, выполните [действия для исключения классического приложения](/windows/security/information-protection/windows-information-protection/create-wip-policy-using-intune-azure#exempt-apps-from-a-wip-policy).

## <a name="create-a-wip-exempt-applocker-policy-file"></a>Создание файла политики AppLocker для исключения из WIP

Так как Visual Studio включает в себя несколько двоичных файлов, [создайте файл политики AppLocker для исключения из WIP](/windows/security/threat-protection/windows-defender-application-control/applocker/run-the-automatically-generate-rules-wizard). AppLocker позволяет автоматически создавать правила для всех файлов в папке.

## <a name="add-appcompat-to-the-enterprise-cloud-resource-policy"></a>Добавление AppCompat в политику корпоративных облачных ресурсов

Чтобы указать, где Visual Studio может обращаться к корпоративным данным в сети, выполните следующие [действия для определения, где защищенные приложения могут находить и отправлять корпоративные данные](/windows/security/information-protection/windows-information-protection/create-wip-policy-using-intune-azure#choose-where-apps-can-access-enterprise-data). Чтобы запретить Windows блокирование подключений к облачным ресурсам через IP-адрес, обязательно добавьте в параметр строку /\*AppCompat\*/.

## <a name="see-also"></a>См. также раздел

- [Поведение приложения с поддержкой WIP](/windows/security/information-protection/windows-information-protection/app-behavior-with-wip)
