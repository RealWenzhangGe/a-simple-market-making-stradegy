# a-simple-market-making-stradegy
so simple that it's not supposed to be used into real market (and not complete yet lol im so lazy)

class market_making():
    def __init__(self, mid_class):
        self.exchange = mid_class
        self.done_amount = 0
        self.init_time = time.time()

    def matched_orders(self, trade_dict):
        self.exchange.create_order('buy', trade_dict['price'], trade_dict['amount'])
        self.exchange.create_order('sell', trade_dict['price'], trade_dict['amount'])
        self.done_amount += trade_dict['amount']
        self.last_time = time.time()

    def make_matched_orders_dict(self, amount, each_amount):
        self.exchange.refresh_data()
        order_price = (self.exchange.sell + self.exchange.buy) / 2
        if order_price > self.exchange.buy and order_price < self.exchange.sell
            self.order_amount = self.exchange.amount
            self.balance = self.exchange.balance
            self.max_order_amount = self.balance / order_price
            make_trade = self.order_amount > each_amount
            make_trade = self.max_order_amount > each_amount
            trade_dict = {'Price':trade_price, 'Amount':each_amount}

        if make_trade:
            self.matched_orders(trade_dict)
