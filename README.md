# hotel.py
#A program for automating the operation of hotels, hotels, guest houses, including management, administration, automatic calculation and much more.
class Hotel:
    def __init__(self, rooms):
        self.rooms = rooms
    def getFreeRooms(self):
        print("List of available rooms: ")
        for room in self.rooms:
            if not room.reserved:
                print(room.number)
    def reserveRoom(self):
        roomNumber = int(input("Enter the room number: "))
        error = True
        for room in self.rooms:
            if roomNumber == room.number and not room.reserved:
                room.reserved = True
                print(f"Комната {room.number} booked")
                error = False
        if error:
            print("Error when booking a room")
    def getReservedRooms(self):
        print("List of rooms booked: ")
        for room in self.rooms:
            if room.reserved:
                print(room.number)
class Room:
    def __init__(self, number, place, tv, wifi):
        self.number = number
        self.place = place
        self.tv = tv
        self.wifi = wifi
        self.reserved = False

hotel = Hotel( [
    Room(11, 3, True, True),
    Room(12, 2, False, False),
    Room(13, 2, False, True),
    Room(21, 1, True, True),
    Room(22, 1, False, False),
    Room(23, 3, False, True),
    Room(31, 2, True, True),
    Room(32, 3, True, False),
    Room(33, 1, True, True)
] )


command = input("Enter the command: ")
while command != 'exit':
    if command == "getFreeRooms":
        hotel.getFreeRooms()
    elif command == "reserveRoom":
        hotel.reserveRoom()
    elif command == "getReservedRooms":
        hotel.getReservedRooms()
    command = input("Enter the command: ")
