overlay
=========

---
  
  
# TEST
  
** インストールが終わったら。。。 **
  
  
** どうするですか。  **


---

Gentooのパケージを作りたいのに、でもパケージシリーチャンジは怖いです。
Gentooのマインパケージシリーの

オーバーレイはなんですか
--------

- overlayは追加のportage repositoryです。
- ここに自分のebuildを追加ができます。

---

ローカルオーバーレイの作り方
--------

** make.confに設定します。 **

    # PORTDIR_OVERLAY="/usr/local/portage/"

このダイレクトリにPortageが追加のpackageを探しています。


** ダイレクトリをつくります。 **

    # mkdir -p /usr/local/portage/app-misc/hello-world 
    # cd $_
    
    $_ recalls last argument

** ebuildのテンプレを作ります。 **

    # cp /usr/portage/header.txt ./hello-world-1.0.ebuild

** これだけ動かない。 **

    # echo 'SLOT="0"' >> ./hello-world-1.0.ebuild


---

オーバーレイの作り方
--------

** オーバーレイのソフトをインストルします。**

    # emerge layman

バージョン管理システムのためUSE FLAGを選びます。

** make.conf ファイルの中でlaymanダイレクトリを追加します。 **

    # echo "source /var/lib/layman/make.conf" >> /etc/portage/make.conf

** Laymanの設定をします。 **

    # vim /etc/layman/layman.cfg
    overlays  : file:///var/lib/layman/my-list.xml
追加をします。

---

** my-list.xml **

    <?xml version="1.0" ?>  
    <repositories version="1.0">  
        <repo priority="50" quality="experimental" status="unofficial">  
            <name>aliceinwire</name>  
            <description>Custom stuff for Gentoo from aliceinwire.</description>  
            <homepage>http://github.com/aliceinwire/</homepage>  
            <owner>  
                <email>alice.ferrazzi@gmail.com</email>  
            </owner>  
            <source type="git">git@github.com:aliceinwire/overlay.git</source>  
        </repo>  
    </repositories>  

---

Proxy-maintainer
--------

https://wiki.gentoo.org/wiki/Project:Proxy_Maintainers

