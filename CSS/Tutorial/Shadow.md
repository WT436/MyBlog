# Shadow Effects

- Với CSS, bạn có thể thêm bóng vào văn bản và các phần tử.
- Trong các chương này, bạn sẽ tìm hiểu về các thuộc tính sau
- text-shadow
- box-shadow

# Text Shadow

- nó sẽ có tác dụng với văn bản

```console
p {
  text-shadow: 2px 2px;
  text-shadow: 2px 2px red;
  text-shadow: 2px 2px 5px red;
  text-shadow: 2px 2px 4px #000000;
  text-shadow: 0 0 3px #FF0000;
  text-shadow: 0 0 3px #FF0000, 0 0 5px #0000FF;
  text-shadow: 1px 1px 2px black, 0 0 25px blue, 0 0 5px darkblue;
  text-shadow: -1px 0 black, 0 1px black, 1px 0 black, 0 -1px black;
}
```

# Box Shadow

- nó dùng cho box của các thẻ

- dùng tương tụ như text
