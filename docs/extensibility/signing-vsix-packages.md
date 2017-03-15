---
title: "Подписывание пакетов VSIX | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- signature
- signing
- authenticode
- vsix
- packages
ms.assetid: e34cfc2c-361c-44f8-9cfe-9f2be229d248
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: da489f0fd0483cddbefb2899eb91bd1d56735d62
ms.lasthandoff: 02/22/2017

---
# <a name="signing-vsix-packages"></a>Подписывание пакетов VSIX
Сборки расширений не обязательно должны быть подписаны, прежде чем они могут работать в Visual Studio, но рекомендуется сделать это.  
  
 Если вы хотите защитить расширения и убедитесь, что оно не было изменено, можно добавить цифровую подпись в пакет VSIX. При подписании VSIX установщик VSIX будет выведено сообщение, указывающее, что он подписан, а также дополнительные сведения о подписи сам. Если содержимое VSIX были изменены, а VSIX снова не подписаны, установщик VSIX показано, что подпись не является допустимым. Установка не завершается, но пользователь получает предупреждение.  
  
> [!IMPORTANT]
>  Начиная с 2015 г., пакеты VSIX, подписанное с помощью отличное SHA256 шифрования определяются имеет недопустимую подпись. Установка VSIX не блокируется, но пользователь будет отображено предупреждение.  
  
## <a name="signing-a-vsix-with-vsixsigntool"></a>Подписи VSIX с VSIXSignTool  
 SHA256 шифрование, подписывание средству [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) на nuget.org в [VsixSignTool](http://www.nuget.org/packages/Microsoft.VSSDK.Vsixsigntool).  
  
#### <a name="to-use-the-vsixsigntool"></a>Использование VSIXSignTool  
  
1.  Добавление в проект вашего VSIX.  
  
2.  Щелкните правой кнопкой мыши узел проекта в обозревателе решений, выбрав **добавить | Управление пакетами NuGet**.  Дополнительные сведения о NuGet и добавление NuGet см. пакеты [NuGet Обзор](http://docs.nuget.org/) и [управление пакетами NuGet с помощью диалогового окна](http://docs.nuget.org/Consume/Package-Manager-Dialog).  
  
3.  Поиск VSIXSignTool из VisualStudioExtensibility и установите пакет NuGet.  
  
4.  Теперь можно запустить VSIXSignTool из расположения локальные пакеты проекта. Обратитесь к разделам справки командной строки средства для подписывания сценария (VSIXSignTool.exe /?).  
  
 Например, для входа с паролем защищенного файла сертификата:  
  
 /F входа VSIXSignTool.exe \<certfile настроек /p \<пароль настроек \<VSIXfile настроек  
  
## <a name="see-also"></a>См. также  
 [Расширения Visual Studio доставки](../extensibility/shipping-visual-studio-extensions.md)
