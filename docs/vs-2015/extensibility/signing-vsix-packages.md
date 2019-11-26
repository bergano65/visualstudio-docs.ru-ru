---
title: Подписывание пакетов VSIX | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b74222804e9ed42e6f8263cbe6ad0daf19cda81f
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300324"
---
# <a name="signing-vsix-packages"></a>Подписывание пакетов VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Сборки расширений не обязательно должны быть подписаны, прежде чем они смогут работать в Visual Studio, но это рекомендуется сделать.  
  
 Если вы хотите защитить расширение и убедиться, что оно не было изменено, можно добавить цифровую подпись к пакету VSIX. Если VSIX подписан, установщик VSIX отобразит сообщение о том, что оно подписано, а также дополнительные сведения о самой сигнатуре. Если содержимое VSIX было изменено и VSIX еще не подписан, установщик VSIX покажет, что подпись недействительна. Установка не остановлена, но пользователь получает предупреждение.  
  
> [!IMPORTANT]
> Начиная с 2015, пакеты VSIX, подписанные с помощью любого объекта, отличного от шифрования SHA256, будут идентифицированы как имеющие недопустимую подпись. Установка VSIX не заблокирована, но пользователь получит предупреждение.  
  
## <a name="signing-a-vsix-with-vsixsigntool"></a>Подписывание VSIX с помощью Всикссигнтул  
 Существует инструмент для подписи шифрования SHA256, доступный в [висуалстудиоекстенсибилити](https://www.nuget.org/profiles/VisualStudioExtensibility) на NuGet.org по адресу [всикссигнтул](https://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool).  
  
#### <a name="to-use-the-vsixsigntool"></a>Использование Всикссигнтул  
  
1. Добавьте VSIX в проект.  
  
2. Щелкните правой кнопкой мыши узел проекта в обозреватель решений, выберите **Добавить &#124; Управление пакетами NuGet**.  Дополнительные сведения о NuGet и добавлении пакетов NuGet см. в статье [Общие сведения о NuGet](https://docs.microsoft.com/nuget/) и [Управление пакетами NuGet с помощью диалогового окна](https://docs.microsoft.com/nuget/consume-packages/install-use-packages-visual-studio).  
  
3. Выполните поиск по запросу Всикссигнтул из Висуалстудиоекстенсибилити и установите пакет NuGet.  
  
4. Теперь можно запустить Всикссигнтул из расположения локальных пакетов проекта. Сведения о сценарии подписывания (Всикссигнтул. exe/?) см. в справке командной строки средства.  
  
   Например, чтобы подписать файл сертификата, защищенный паролем:  
  
   Всикссигнтул. exe Sign/f \<CertFile >/p \<пароль > \<Всиксфиле >  
  
## <a name="see-also"></a>См. также  
 [Доставка расширений Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
