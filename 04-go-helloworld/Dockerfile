
# 使用したいイメージのベース。Ubuntu,Node.js,Rubyとか。
# ここで書いてるimageはすでにDockerがインストールされてたり、誰かが手を加えているので便利な状態となっている。
FROM golang:1.16 AS builder

# コンテナ内の作業ディレクトリを決める
WORKDIR /

# ファイルをコンテナの方にコピー。COPY [ホスト側のパス] [コンテナ側のパス]と書く
COPY go.mod ./
COPY ./hello.go .


# hello.goをbuildする
RUN go build -o hello .

FROM alpine:3.22.0
WORKDIR /root/
COPY --from=builder /hello ./
# CMDはコンテナ起動時に実行されるコマンド。ここではhelloが実行される。パス指定はコンテナ内のやつ
CMD ["./hello"]