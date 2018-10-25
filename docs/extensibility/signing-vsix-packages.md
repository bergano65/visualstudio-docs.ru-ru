---
title: Подписывание пакетов VSIX | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6520171619833fe3c74f87634e9e83c24da33d70
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49855941"
---
# <a name="signing-vsix-packages"></a>Подписывание пакетов VSIX
Расширения сборки не обязательно должны быть подписаны, прежде чем они могут работать в Visual Studio, но рекомендуется сделать это.  
  
 Если вы хотите защитить ваше расширение и убедитесь, что оно не было изменено, можно добавить цифровую подпись в пакет VSIX. При подписании VSIX, установщик VSIX отобразит сообщение о том, что он подписан, а также дополнительные сведения о сама подпись. Если содержимое VSIX были изменены, а VSIX снова не подписана, установщик VSIX покажет, что подпись не является допустимым. Установка не прекращается, но пользователь получает предупреждение.  
  
> [!IMPORTANT]
>  Начиная с Visual Studio 2015, подписываются с использованием ничего, кроме SHA256 шифрование пакетов VSIX будет определяться как имеющий недопустимую подпись. Установка VSIX не блокируется, но пользователь отображается предупреждение.  
  
## <a name="signing-a-vsix-with-vsixsigntool"></a>Подписи VSIX с VSIXSignTool  
 SHA256 шифрование, подписи средство, доступное из [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) на сайте nuget.org в [VsixSignTool](http://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool).  
  
#### <a name="to-use-the-vsixsigntool"></a>Чтобы использовать VSIXSignTool  
  
1. Добавление в проект VSIX.  
  
2. Щелкните правой кнопкой мыши узел проекта в обозревателе решений, выбрав **добавить &#124; управление пакетами NuGet**.  Дополнительные сведения о NuGet и добавлении NuGet пакетов см. в разделе [документации по NuGet](/NuGet) и [пользовательский Интерфейс диспетчера пакетов](/NuGet/Tools/Package-Manager-UI) разделы.  
  
3. Поиск VSIXSignTool из VisualStudioExtensibility и установите пакет NuGet.  
  
4. Теперь можно запустить VSIXSignTool из расположения локальные пакеты проекта. См. справку командной строки средства для подписывания сценария (VSIXSignTool.exe /?).  
  
   Например подписать с помощью сертификата, защищенный файл пароля:  
  
   /F входа VSIXSignTool.exe \<certfile > /p \<пароль > \<VSIXfile >  
  
## <a name="see-also"></a>См. также  
 [Доставка расширений Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
