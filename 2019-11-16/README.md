# ʹ��Rust��Substrate�����򵥵ļ���è��Ϸ

## Substrate��������
### ��װ����
�ο�[Minimal substrate development environment setup](https://github.com/darwinia-network/workshop/blob/master/minimal-substrate-development-environment-setup/README.md)

## ����Substrate�ڵ�
���������ݶ�Ϊsubstratekitties
```sh
 #ʹ�ýű��ļ�������runtime��ģ��ڵ�
 substrate-node-new substratekitties <your name>
 cd substratekitties
```
## ��������ɵļ���è��Լ����
```sh
git clone https://github.com/darwinia-network/workshop.git
#�����زֿ��е�substratekitties.rs��ֵ���Ƶ��½ڵ��runtime/src��
cp <your path>/workshop/substratekitties.rs <your path>/substratekitties/runtime/src/
```
## ��lib.rs�����ģ��
```rust
//�����Module
mod substratekitties;
//ʵ��trait
impl substratekitties::Trait for Runtime{
	type Event = Event;
}
//��construct_runtime!���������ǵ�ģ��
construct_runtime!{
	puub enum Runtime with Log(InternalLog: DigestItem<Hash, AuthorityId, AuthoritySignature>)
	where ...
		...
		...{
		Substratekitties : substratekitties::{Module,Call,Storage,Event<T>};
	}
}
```

## ��������
```sh
#�򿪹���Ŀ¼
cd substratekitties
#�����Wasm�ļ�
#����ǵ�һ��ʹ�ýڵ㣬Ҫ��ִ��./scripts/init.sh
./scripts/build.sh
#����ɶ������ļ�
cargo build --release
#�����ڵ�
./target/release/substratekitties --dev
#����˴���Ϊ���ڶ��������޸ĺ�ĸ��£��������
./target/release/substratekitties purge-chain --dev
```

## �鿴
����https://polkadot.js.org/apps/#/explorer

Settings -> remote node/endpoint to connect to -> Locol Host
![example](https://github.com/Eanam/workshop/blob/master/2019-11-16/pics/Setting.png?raw=true)

## ��������
��������һ�ֶ���������ڸ��µķ�����Substrate�ṩ��һ�ָ��򵥵������ķ�����������������������޷ֲ��ʵʱ������
```sh
#�����Wasm Runtime�ļ�
./scripts/build.sh
#����<your path>/substratekitties/runtime/wasm/target/wasm32-unknown-unknown/release/
#�ɹ۲쵽һ���µ�compact Wasm Binary
```
����Wasm�ļ���ק�����½���ָ��λ�ú�����ύ��ˢ�º�����Թ۲쵽���µ����ݣ�
![update](https://raw.githubusercontent.com/Eanam/workshop/master/2019-11-16/pics/Update.png)

:heavy_exclamation_mark: ����Ҫӵ��sudo��Ȩ�ޣ�����Sudo -> Set sudo key�²鿴





