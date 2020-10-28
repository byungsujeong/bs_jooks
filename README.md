# bs_jooks

## description

Collection of awesome React Hooks ready to install with NPM

## example

https://4rg0u.csb.app/

const App = () => {
  const sayHello = () => console.log("hello");
  const { currentItem, changeItem } = useTaps(0, content);
  const [number, setNumber] = useState(0);
  const [aNumber, setANumber] = useState(0);
  useEffect(sayHello, [currentItem, aNumber]);
  const titleUpdater = useTitle("Loading...");
  setTimeout(() => titleUpdater("Home"), 5000);
  const input = useRef();
  const title = useClick(sayHello);
  const deleteWorld = () => console.log("del!!!");
  const abort = () => console.log("Aborted");
  const confirmDelete = useConfirm("Are you sure?", deleteWorld, abort);
  const { enablePrevent, disablePrevent } = usePreventLeave();
  const begForLife = () => console.log("Pls dont leave");
  useBeforeLeave(begForLife);
  const fadeInH2 = useFadeIn(2, 1);
  const handleNetworkChange = (online) => {
    console.log(online ? "We just wnet online" : "We are offline");
  };
  const onLine = useNetwork(handleNetworkChange);
  const { y } = useScroll();
  const { element, triggerFull, exitFull } = useFullscreen();
  const triggerNotif = useNotification("Too much", {
    body: "right?"
  });
  const { loading, data, error, refetch } = useAxios({
    url: "https://reqres.in/api/products/3"
  });

  return (
    <div className="App">
      <button onClick={triggerNotif}>Notification</button>
      <h1>{onLine ? "Online" : "Offline"}</h1>
      <h2 {...fadeInH2}>Hi</h2>
      <h3 ref={title}>Click</h3>
      <div>
        <button onClick={() => setNumber(number + 1)}>{number}</button>
        <button onClick={() => setANumber(aNumber + 1)}>{aNumber}</button>
      </div>
      {content.map((section, index) => (
        <button onClick={() => changeItem(index)}>{section.tab}</button>
      ))}
      <div>{currentItem.content}</div>
      <div>
        <input ref={input} placeholder="la" />
      </div>
      <div>
        <button onClick={confirmDelete}>Delete the world</button>
      </div>
      <div>
        <button onClick={enablePrevent}>Protect</button>
        <button onClick={disablePrevent}>Unprotect</button>
      </div>
      <img
        onClick={triggerFull}
        onDoubleClick={exitFull}
        ref={element}
        src="https://search.pstatic.net/sunny/?src=https%3A%2F%2Fi.pinimg.com%2Foriginals%2Feb%2F52%2Fc9%2Feb52c9dc6fea3c4b41c7552e706d9f17.jpg&type=b400"
      />
      <div style={{ height: "1000vh" }}>
        <h3 style={{ position: "fixed", color: y > 100 ? "red" : "blue" }}>
          Color
        </h3>
        <h2>{data && data.status}</h2>
        <div>
          <button onClick={refetch}>Refetch</button>
        </div>
      </div>
    </div>
  );
};

